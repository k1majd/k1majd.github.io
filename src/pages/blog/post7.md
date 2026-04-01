---
layout: "../../layouts/BlankLayout.astro"
title: "Safe Model Predictive Diffusion with Shielding"
description: "A training-free diffusion planner that generates provably safe and kinodynamically feasible trajectories by integrating a safety shield into the denoising process."
pubDate: "Apr 1 2026"
heroImage: "/projects/safe_mpd/teaser.png"
badge: "ICRA'26"
---
<div class="mb-5">
    <h2 style="text-align:center " id="center" class="text-3xl w-full font-bold ">Safe Model Predictive Diffusion with Shielding</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold "><a
        href="https://www.taekyung.me"
        >T. Kim</a
      >, <a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, H. Okamoto, <a
        href="https://www.bhoxha.com"
        >B. Hoxha</a
      >, <a
        href="https://dpanagou.engin.umich.edu"
        >D. Panagou</a
      >, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      ></h2>
  </div>
<div>
    <img
        src="/projects/safe_mpd/teaser.png"
        alt="Safe MPD teaser"
    />
</div>
<br />
<div>
<div class="mb-10 text-justify">
    <b> Abstract:</b>
     Generating safe, kinodynamically feasible, and optimal trajectories for complex robotic systems is a central challenge in robotics. This paper presents Safe Model Predictive Diffusion (Safe MPD), a training-free diffusion planner that unifies a model-based diffusion framework with a safety shield to generate trajectories that are both kinodynamically feasible and safe by construction. By enforcing feasibility and safety on all samples during the denoising process, our method avoids the common pitfalls of post-processing corrections, such as computational intractability and loss of feasibility. We validate our approach on challenging non-convex planning problems, including kinematic and acceleration-controlled tractor-trailer systems. Through parallelization on GPU, our method achieves sub-second planning times even on challenging, non-convex problems.
  </div>
<div class="center">
    <div id="col_inner_id-safempd" class="fw-col-inner" data-paddings="0px 0px 0px 0px">
        <a href="https://www.taekyung.me/safe-mpd" target="_blank" class="btn btn-outline" data-mtop="0" data-mbottom="0">Project Page</a>
        <a href="https://arxiv.org/abs/2512.06261" target="_blank" class="btn btn-outline" data-mtop="0" data-mbottom="0">Full Paper (arXiv)</a>
        <a href="https://github.com/cps-atlas/safe-mpd" target="_blank" class="btn btn-outline" data-mtop="0" data-mbottom="0">Source Code</a>
        <a href="https://youtu.be/DQBeybU7EYI" target="_blank" class="btn btn-outline" data-mtop="0" data-mbottom="0">Video</a>
    </div>
</div>
<br />
<br />
<div><iframe width="800" height="450" src="https://www.youtube.com/embed/DQBeybU7EYI" title="Safe Model Predictive Diffusion with Shielding" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></div>
<br />
<br />
</div>
  <div class="mb-5">
    <div class="text-2xl w-full font-bold">Publication</div>
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
