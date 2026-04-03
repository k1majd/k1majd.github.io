---
layout: "../../layouts/BlankLayout.astro"
title: "GPU-Accelerated Safe Motion Planning for Articulated Vehicles"
description: "A unified GPU-accelerated motion planning platform for tractor-trailer systems, combining Safe Model Predictive Diffusion for global planning with Barrier-Rate MPPI for real-time trajectory tracking."
pubDate: "Apr 1 2026"
heroImage: "/projects/safe_mpd/teaser.gif"
badge: "ICRA'26 - ITSC'25"
---
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="text-3xl w-full font-bold">GPU-Accelerated Safe Motion Planning for Articulated Vehicles</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold"><a
        href="https://www.taekyung.me/"
        >T. Kim</a
      >, <a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, <a
        href="https://hamidreza-p.github.io/"
        >H. Parwana</a
      >, B. Hoxha, S. Hong, H. Okamoto, <a
        href="https://dpanagou.engin.umich.edu/"
        >D. Panagou</a
      >, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      ></h2>
  </div>
<div style="display:flex; justify-content:center; align-items:center; gap:1.5rem;" class="mb-4">
<img src="/logos/images.jpeg" alt="Toyota Logo" style="height:36px; width:auto;" />
<img src="/logos/University-of-Michigan-Logo-500x281.png" alt="University of Michigan Logo" style="height:80px; width:auto;" />
</div>
<div>
    <img
        src="/projects/safe_mpd/teaser.gif"
        alt="Safe MPD integrated with BR-MPPI on a tractor-trailer in CarMaker"
    />
</div>
<br />

<div class="mb-10 text-justify">

  <h3 class="text-xl font-bold mb-3">Motivation</h3>

  <p class="mb-4">Articulated vehicles such as tractor-trailers must routinely reverse and maneuver in cluttered environments such as parking lots, loading docks, and narrow corridors. This demands a motion planning system that is simultaneously <b>safe</b> (collision-free with formal guarantees), <b>kinodynamically feasible</b> (respecting the vehicle's complex, nonholonomic dynamics), and <b>real-time</b> (fast enough for closed-loop control).</p>

  <p class="mb-4">Classical planners can provide safety guarantees but are often computationally expensive, especially in non-convex environments with many obstacles. On the other hand, recent diffusion-based planners are powerful at generating high-quality trajectories but typically lack formal safety guarantees, and common workarounds like guidance or projection either break kinodynamic feasibility or are computationally intractable.</p>

  <p class="mb-4">In this line of work, we propose a <b>unified GPU-accelerated motion planning platform</b> that addresses both challenges. The platform consists of two complementary modules:</p>

  <ul class="list-disc ml-6 mb-6">
    <li class="mb-2"><b>Safe Model Predictive Diffusion (Safe MPD):</b> a high-level planner that generates globally optimal, provably safe reference paths in sub-seconds using diffusion-based sampling with an integrated safety shield.</li>
    <li class="mb-2"><b>Barrier-Rate MPPI (BR-MPPI):</b> a low-level controller that tracks the reference path in real-time (100+ Hz) while maintaining safety through Control Barrier Function constraints embedded directly in the MPPI importance-sampling update.</li>
  </ul>

  <p class="mb-4">Both modules are fully parallelized on a single GPU. Safe MPD replaces classical global planners that would be computationally costly, producing high-quality reference trajectories in sub-seconds. The generated global path is then passed to BR-MPPI for real-time tracking and reactive control. Together, they form a complete planning-to-control pipeline validated on a 12m tractor-trailer in the high-fidelity CarMaker simulator.</p>

  <hr class="my-8" />

  <h3 class="text-xl font-bold mb-3">High-Level Planner: Safe Model Predictive Diffusion</h3>

  <p class="mb-4">Safe MPD is a training-free diffusion planner that unifies a model-based diffusion framework with a safety shield, called Shielded Rollout, to generate trajectories that are both kinodynamically feasible and safe by construction. By enforcing feasibility and safety on all samples <i>throughout</i> the denoising process (not as a post-hoc correction) Safe MPD avoids the pitfalls of guidance (loss of feasibility) and projection (computational intractability in non-convex environments). The planner's design centers on three key ideas:</p>

  <p class="mb-2"><b>1. Training-Free Model-Based Score Estimation.</b> Unlike standard diffusion models that learn a neural network from expert demonstrations, Safe MPD leverages the known dynamics model and cost function to compute the score function directly via Monte Carlo approximation. At each denoising step, K candidate trajectories are drawn around the current noisy estimate, scored using the true objective, and used to perform a principled weighted-average update. This training-free formulation eliminates the need for data collection and naturally supports test-time adaptation to new tasks and environments without retraining.</p>

  <p class="mb-2"><b>2. Shielded Rollout for Provable Safety.</b> The core innovation is the Shielded Rollout mechanism, inspired by model predictive shielding. At each time step during forward simulation, before accepting a nominal control input from the diffusion process, the algorithm simulates a finite-horizon rollout under a backup policy to verify that the system can be brought back to a controlled-invariant safe set. If this validity check passes, meaning the trajectory stays within the safe set and reaches the invariant set within the backup horizon, the nominal input is accepted. Otherwise, the backup policy takes over for the remainder of the trajectory. This provides a formal guarantee that the system remains safe for all future time in each rollout.</p>

  <p class="mb-4"><b>3. In-Process Safety Enforcement.</b> Rather than applying safety corrections only to the final output (as in filtering, guidance, or projection methods), Safe MPD integrates the Shielded Rollout at two stages: (i) within every denoising step on all K candidate samples, and (ii) on the final diffusion output. Because every shielded sample is guaranteed to be feasible and safe, the feasibility and safety probability terms become constant across all samples and can be dropped from the target distribution which then simplifies to depend solely on the cost objective. This dramatically improves sample efficiency, since no computational effort is wasted on samples that would otherwise receive zero weight from constraint violations. The iterative score ascent also helps the optimizer overcome local minima while shielding preserves safety at every step.</p>

  <p class="mb-4">Through GPU parallelization of all K candidate rollouts and their shielded validity checks, Safe MPD achieves sub-second planning times even on challenging non-convex problems with dozens of obstacles that makes it a practical replacement for classical global planners.</p>

<div class="my-6">
<img src="/projects/safe_mpd/safe_mpd_overview.png" alt="Overview of Safe MPD: forward noising process and backward denoising with Shielded Rollout on K parallel GPU samples" style="width:100%; border-radius:4px;" />
<p class="text-xs font-light text-center mt-1 italic" style="line-height:1.3;">Overview of Safe MPD. Top: the forward process adds noise to an optimal trajectory. Bottom: the reverse (denoising) process with Shielded Rollout — K candidates are drawn on GPU; unsafe ones (red) are transformed into safe, feasible trajectories (blue) before weighted averaging and score ascent.</p>
</div>

  <div class="center mb-4">
    <a href="https://www.taekyung.me/safe-mpd" target="_blank" class="btn btn-outline">Project Page</a>
    <a href="https://arxiv.org/abs/2512.06261" target="_blank" class="btn btn-outline">Paper (arXiv)</a>
    <a href="https://github.com/cps-atlas/safe-mpd" target="_blank" class="btn btn-outline">Source Code</a>
    <a href="https://youtu.be/DQBeybU7EYI" target="_blank" class="btn btn-outline">Video</a>
  </div>

  <hr class="my-8" />

  <h3 class="text-xl font-bold mb-3">Low-Level Controller: Barrier-Rate MPPI</h3>

  <p class="mb-4"><a href="https://arxiv.org/pdf/2506.07325">BR-MPPI</a> is a GPU-accelerated sampling-based controller that embeds Control Barrier Function (CBF) constraints directly into the Model Predictive Path Integral (MPPI) importance-sampling distribution. Rather than rejecting unsafe samples or penalizing collisions after the fact, BR-MPPI steers the sampling distribution itself toward collision-free, dynamically feasible trajectories. This fundamentally improves the exploration strength of MPPI and produces more robust control inputs. The controller's design centers on three key elements:</p>

<div style="float:right; width:320px; margin:0 0 1rem 1.5rem;">
<img src="/projects/safe_mpd/br_vs_vanilla.jpg" alt="BR-MPPI vs Standard MPPI rollout comparison during backward parking" style="width:100%; border-radius:4px;" />
<p class="text-xs font-light text-center mt-1 italic" style="line-height:1.3;">BR-MPPI (left) projects rollouts outside obstacle regions; standard MPPI with collision cost (right) collides in tight spaces.</p>
</div>

  <p class="mb-2"><b>1. BR-MPPI Sampling with Projected Rollouts.</b> Standard MPPI penalizes collisions through soft costs in the objective, which struggles in tight spaces because most random samples violate constraints. BR-MPPI instead converts each CBF inequality constraint into a parameterized equality constraint with a time-varying barrier rate &alpha;. During each rollout, the sampled control inputs are <i>projected</i> onto the safe manifold defined by these equality constraints via a weighted minimum-norm problem that admits a closed-form solution. Actuator bounds are incorporated as soft penalties within this projection, keeping the solution analytical and GPU-friendly. The result is that all rollouts per step are steered toward collision-free trajectories <i>by construction</i>, rather than relying on cost penalties to discourage unsafe ones.</p>

  <p class="mb-2"><b>2. Contouring Cost for Path Tracking.</b> Instead of naively tracking a time-parameterized reference trajectory which can accumulate error and cause sudden corrections (especially in reverse), we adopt a contouring cost formulation. The cost jointly minimizes the <i>contouring error</i> (perpendicular distance to the reference path), the <i>lag error</i> (longitudinal distance behind the nearest path point), and heading deviations for both tractor and trailer. An additional progress-rate term encourages steady advancement along the path while allowing temporary slowdowns for safety. This formulation provides a tunable trade-off between tracking accuracy and forward progress, and is robust to the path parameterization issues that plague standard trajectory tracking in reverse maneuvers.</p>

  <p class="mb-4"><b>3. Hitch Angle Stabilizer.</b> Reverse parking is inherently unstable for tractor-trailer systems: small steering deviations can cause large, uncontrolled articulations leading to jackknifing. To prevent this, we add a velocity-dependent hitch angle constraint (the maximum allowable hitch angle shrinks as speed increases). This constraint is enforced through a CBF-based Quadratic Program (CBF-QP) that filters BR-MPPI's control outputs at each time step, ensuring the hitch angle remains within a safe range.</p>

<div style="clear:both;"></div>

  <p class="mb-4">On a single GPU, BR-MPPI computes control inputs at over 100 Hz (for scenarios with eight obstacles) using 5,000 parallel rollouts with a 4.8-second prediction horizon — enabling real-time closed-loop control for the full tractor-trailer system including reverse maneuvers.</p>

  <div class="center mb-4">
    <a href="https://arxiv.org/abs/2508.05773" target="_blank" class="btn btn-outline">Paper (arXiv)</a>
  </div>

  <hr class="my-8" />

  <h3 class="text-xl font-bold mb-3">Unified Platform</h3>

  <p class="mb-4">The key insight behind this platform is that <b>both planning and control can be cast as GPU-parallelizable sampling problems</b>. Safe MPD samples thousands of trajectory candidates during diffusion denoising, while BR-MPPI samples thousands of control rollouts during path-integral optimization. By keeping the entire pipeline on the GPU, we eliminate the latency of transferring data between heterogeneous compute units and achieve end-to-end real-time performance.</p>

  <p class="mb-4">We validated the integrated system in CarMaker on a 12m tractor-trailer performing reverse and forward parking in a cluttered parking lot. Safe MPD generates the collision-free reference path in sub-seconds, and BR-MPPI tracks it in real time while maintaining formal safety via CBF constraints, all on a single GPU.</p>

</div>

<div><iframe width="800" height="450" src="https://www.youtube.com/embed/DQBeybU7EYI" title="Safe Model Predictive Diffusion with Shielding" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></div>
<br />
<br />

  <div class="mb-5">
    <div class="text-2xl w-full font-bold">Publications</div>
  </div>
  <div class="pub-row">
    <div class="pub-badge"><span class="badge">ICRA'26</span></div>
    <div class="pub-content">
      <h3 class="font-semibold mb-0.2 text-justify">Safe Model Predictive Diffusion with Shielding</h3>
      <p class="font-light text-sm">T. Kim, <ins>K. Majd</ins>, H. Okamoto, B. Hoxha, D. Panagou, G. Fainekos</p>
      <i class="font-light text-sm">IEEE International Conference on Robotics and Automation (ICRA), 2026.</i>
      <a href="/bib/icra26.txt">BibTex</a>
    </div>
  </div>

  <div class="pub-row">
    <div class="pub-badge"><span class="badge">ITSC'25</span></div>
    <div class="pub-content">
      <h3 class="font-semibold mb-0.2 text-justify">GPU-Accelerated Barrier-Rate Guided MPPI Control for Tractor-Trailer Systems</h3>
      <p class="font-light text-sm"><ins>K. Majd</ins>, H. Parwana, B. Hoxha, S. Hong, H. Okamoto, G. Fainekos</p>
      <i class="font-light text-sm">IEEE International Conference on Intelligent Transportation Systems (ITSC), 2025.</i>
      <a href="/bib/itsc25.txt">BibTex</a>
    </div>
  </div>
