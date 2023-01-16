---
layout: "../../layouts/BlankLayout.astro"
title: "Safe Robot Learning in Assistive Devices through Neural Network Repair"
description: "This project presents NNRepLayer: the first repair technique applied to a real physical system."
pubDate: "Dec 6 2022"
heroImage: "/projects/nnreplayer_prosthesis/tumb1.png"
---
<style>
    * {
      box-sizing: border-box;
    }

    /* Create two unequal columns that floats next to each other */
    .column {
      float: left;
      padding: 1px;
    }

    .left {
      width: 13%;
    }

    .right {
      width: 87%;
    }

    /* Clear floats after the columns */
    .row:after {
      content: "";
      display: table;
      clear: both;
    }
</style>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="text-4xl w-full font-bold ">Safe Robot Learning in Assistive Devices through Neural Network Repair</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold "><a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, G. Clark, <a
        href="https://www.daittan.com"
        >T. Khandait</a
      >, <a
        href="https://www.linkedin.com/in/siyu-zhou-a1449962/"
        >S. Zhou</a
      >, <a
        href="https://home.cs.colorado.edu/~srirams/"
        >S. Sankaranarayanan</a
      >, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      >, <a
        href="http://henibenamor.weebly.com"
        >H. Ben Amor</a
      ></h2>
  </div>
<div>
    <img
        src="/projects/nnreplayer_prosthesis/gif1.gif"
        alt="profile image"
    />
</div>
<div>
<div class="mb-10 text-justify">
    <b> Abstract:</b> 
    Guaranteeing safety in human-centric applications is critical in robot learning as the learned policies may demonstrate unsafe behaviors in formerly unseen scenarios. We present a framework to locally repair an erroneous policy network to satisfy a set of formal safety constraints using Mixed Integer Quadratic Programming (MIQP). Our MIQP formulation explicitly imposes the safety constraints to the learned policy while minimizing the original loss function. We demonstrate the application of our framework to derive safe policies for a robotic lower-leg prosthesis. 
  </div>
<div class=" col-xs-12 col-sm-2 ">
<div class="center">
    <div id="col_inner_id-638fba18b86c0" class="fw-col-inner" data-paddings="0px 0px 0px 0px">
		<a href="/papers/CoRL22.pdf" target="_blank" id="button_35873d1d8b5611a5c514ec3437e68163" class="btn btn-primary" data-mtop="0" data-mbottom="0">Full Paper (CoRL)</a>	
        <a href="/papers/Neurips22.pdf" target="_blank" id="button_35873d1d8b5611a5c514ec3437e68163" class="btn btn-primary" data-mtop="0" data-mbottom="0">Full Paper (NeurIPS)</a>	
        <a href="https://github.com/k1majd/NNRepLayer.git" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Source Code</a>
        <a href="https://recorder-v3.slideslive.com/#/share?share=77885&s=05218cda-a354-4f6d-a6fb-8455c79c27ad" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Talk (NeurIPS)</a>
        <a href="/posters/poster_neurips2022.png" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Poster</a></div>
        </div>
</div>
<br />
<br />
<div>
    <img
        src="/projects/nnreplayer_prosthesis/gif2.gif"
        alt="profile image"
    />
</div>
<br />
<br />
</div>
  <div class="mb-5">
    <div class="text-3xl w-full font-bold">Publications</div>
  </div>
  <div class="row">
    <div class="column left">
      <span class="badge">NeurIPS'22</span>
    </div>
    <div class="column right">
      <h3 class="font-semibold mb-0.2 text-justify">
        Certifiably-correct Control Policies for Safe Learning and Adaptation in
        Assistive Robotics
      </h3>
      <span style="color: #ff0000">(Received a Best Paper Award)</span>
      <p class="font-light text-sm">
        <ins>K. Majd</ins>, G. Clark, T. Khandait, S. Zhou, S. Sankaranarayanan,
        G. Fainekos, H. Ben Amor
      </p>
      <i class="font-light text-sm">
        Neural Information Processing Systems (NeurIPS) - Robot Learning
        Workshop, 2022.
      </i>
      <p class="my-2 text-justify"></p>
      <a href="/bib/neurips22.txt">[BibTex]</a>
    </div>
  </div>

  <br />
  <div class="row">
    <div class="column left">
      <span class="badge">CoRL'22</span>
    </div>
    <div class="column right">
      <h3 class="font-semibold mb-0.2 text-justify">
        Safe Robot Learning in Assistive Devices through Neural Network Repair
      </h3>
      <p class="font-light text-sm">
        <ins>K. Majd</ins>, G. Clark, T. Khandait, S. Zhou, S. Sankaranarayanan,
        G. Fainekos, H. Ben Amor
      </p>
      <i class="font-light text-sm">
        Conference on Robot Learning (CoRL), 2022.
      </i>
      <p class="my-2 text-justify"></p>
      <a href="/bib/corl22.txt">[BibTex]</a>
    </div>
  </div>