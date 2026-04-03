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
<div>
    <img
        src="/projects/safe_mpd/teaser.gif"
        alt="Safe MPD integrated with BR-MPPI on a tractor-trailer in CarMaker"
    />
</div>
<br />

<div class="mb-10 text-justify">

  <h3 class="text-xl font-bold mb-3">Motivation</h3>

  <p class="mb-4">Articulated vehicles such as tractor-trailers and yard trucks must routinely reverse and maneuver in cluttered environments — parking lots, loading docks, narrow corridors — where pedestrians may be present. This demands a motion planning system that is simultaneously <b>safe</b> (collision-free with formal guarantees), <b>kinodynamically feasible</b> (respecting the vehicle's complex, nonholonomic dynamics), and <b>real-time</b> (fast enough for closed-loop control).</p>

  <p class="mb-4">Classical planners can provide safety guarantees but are often computationally expensive, especially in non-convex environments with many obstacles. On the other hand, recent diffusion-based planners are powerful at generating high-quality trajectories but typically lack formal safety guarantees — common workarounds like guidance or projection either break kinodynamic feasibility or are computationally intractable.</p>

  <p class="mb-4">In this line of work, we propose a <b>unified GPU-accelerated motion planning platform</b> that addresses both challenges. The platform consists of two complementary modules:</p>

  <ul class="list-disc ml-6 mb-6">
    <li class="mb-2"><b>Safe Model Predictive Diffusion (Safe MPD)</b> — a high-level planner that generates globally optimal, provably safe reference paths in sub-seconds using diffusion-based sampling with an integrated safety shield.</li>
    <li class="mb-2"><b>Barrier-Rate MPPI (BR-MPPI)</b> — a low-level controller that tracks the reference path in real-time (100+ Hz) while maintaining safety through Control Barrier Function constraints embedded directly in the MPPI importance-sampling update.</li>
  </ul>

  <p class="mb-4">Both modules are fully parallelized on a single GPU. Safe MPD replaces classical global planners that would be computationally costly, producing high-quality reference trajectories in sub-seconds. The generated global path is then passed to BR-MPPI for real-time tracking and reactive control. Together, they form a complete planning-to-control pipeline validated on a 12m tractor-trailer in the high-fidelity CarMaker simulator.</p>

  <hr class="my-8" />

  <h3 class="text-xl font-bold mb-3">High-Level Planner: Safe Model Predictive Diffusion (ICRA'26)</h3>

  <p class="mb-4">Safe MPD is a training-free diffusion planner that unifies a model-based diffusion framework with a safety shield, called Shielded Rollout, to generate trajectories that are both kinodynamically feasible and safe by construction. At each denoising step, K candidate trajectories are generated in parallel. The Shielded Rollout mechanism transforms every candidate into a kinodynamically feasible and provably safe trajectory before the Monte Carlo score ascent step. By enforcing feasibility and safety on all samples <i>throughout</i> the denoising process — not as a post-hoc correction — Safe MPD avoids the pitfalls of guidance (loss of feasibility) and projection (computational intractability in non-convex environments).</p>

  <p class="mb-4">Through GPU parallelization, Safe MPD achieves sub-second planning times even on challenging non-convex problems with dozens of obstacles, making it a practical drop-in replacement for classical global planners.</p>

  <div class="center mb-4">
    <a href="https://www.taekyung.me/safe-mpd" target="_blank" class="btn btn-outline">Project Page</a>
    <a href="https://arxiv.org/abs/2512.06261" target="_blank" class="btn btn-outline">Paper (arXiv)</a>
    <a href="https://github.com/cps-atlas/safe-mpd" target="_blank" class="btn btn-outline">Source Code</a>
    <a href="https://youtu.be/DQBeybU7EYI" target="_blank" class="btn btn-outline">Video</a>
  </div>

  <hr class="my-8" />

  <h3 class="text-xl font-bold mb-3">Low-Level Controller: Barrier-Rate MPPI (ITSC'25)</h3>

  <p class="mb-4">BR-MPPI is a GPU-accelerated sampling-based controller that embeds Control Barrier Function (CBF) constraints directly into the Model Predictive Path Integral (MPPI) importance-sampling distribution. Rather than rejecting unsafe samples or penalizing collisions after the fact, BR-MPPI steers the sampling distribution itself toward collision-free, dynamically feasible trajectories. This fundamentally improves the exploration strength of MPPI and produces more robust control inputs.</p>

  <p class="mb-4">Given the global reference path from Safe MPD, BR-MPPI tracks it in real-time while reacting to dynamic obstacles and maintaining safety constraints. On a single GPU, BR-MPPI computes control inputs at over 100 Hz (for scenarios with eight obstacles), enabling closed-loop control for the full tractor-trailer system including reverse maneuvers.</p>

  <div class="center mb-4">
    <a href="https://arxiv.org/abs/2508.05773" target="_blank" class="btn btn-outline">Paper (arXiv)</a>
  </div>

  <hr class="my-8" />

  <h3 class="text-xl font-bold mb-3">Unified Platform</h3>

  <p class="mb-4">The key insight behind this platform is that <b>both planning and control can be cast as GPU-parallelizable sampling problems</b>. Safe MPD samples thousands of trajectory candidates during diffusion denoising, while BR-MPPI samples thousands of control rollouts during path-integral optimization. By keeping the entire pipeline on the GPU, we eliminate the latency of transferring data between heterogeneous compute units and achieve end-to-end real-time performance.</p>

  <p class="mb-4">We validated the integrated system in CarMaker on a 12m tractor-trailer performing reverse and forward parking in a cluttered parking lot. Safe MPD generates the collision-free reference path in sub-seconds, and BR-MPPI tracks it while maintaining formal safety guarantees via CBF constraints — all on a single GPU.</p>

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
