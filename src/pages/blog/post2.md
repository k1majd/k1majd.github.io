---
layout: "../../layouts/BlankLayout.astro"
title: "Risk-bounded Motion Planning and Control in Confined Dynamic Environment"
description: "This project addresses the \"Freezing Robot\" problem in dynamic confined environments. We introduced a method to bound the probability of collision to a given value in finite-time."
pubDate: "Sep 1 2021"
heroImage: "/projects/nnreplayer_prosthesis/tumb2.gif"
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
    <h2 style="text-align:center " id="center" class="text-4xl w-full font-bold ">Risk-bounded Motion Planning and Control in Confined Dynamic Environment</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold "><a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, <a 
        href="https://sites.google.com/asu.edu/syaghoub/home?authuser=0"
        >S. Yaghoubi</a
      >, <a
        href="https://www.linkedin.com/in/tomoya-yamaguchi-6b727645/?originalSubdomain=jp"
        >T. Yamaguchi</a
      >, <a
        href="https://www.bhoxha.com"
        >B. Hoxha</a
      >, <a
        href="https://sites.google.com/site/dvprokhorov/"
        >D. Prokhorov</a
      >, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      ></h2>
  </div>
<div>
    <img
        src="/projects/nnreplayer_prosthesis/tumb3.jpg"
        alt="profile image"
    />
</div>
<div>
<div class="mb-10 text-justify">
    <b> Abstract:</b> 
     Sampling-based methods such as Rapidly-exploring Random Trees (RRTs) have been widely used for generating motion paths for autonomous mobile systems. In this work, we extend time-based RRTs with Control Barrier Functions (CBFs) to generate, safe motion plans in dynamic environments with many pedestrians. Our framework is based upon a human motion prediction model which is well suited for indoor narrow environments. We demonstrate our approach on a high-fidelity model of the Toyota Human Support Robot navigating in narrow corridors. We show in three scenarios that our proposed online method can navigate safely in the presence of moving agents with unknown dynamics. 
  </div>
<div class=" col-xs-12 col-sm-2 ">
<div class="center">
    <div id="col_inner_id-638fba18b86c0" class="fw-col-inner" data-paddings="0px 0px 0px 0px">
		<a href="/papers/IROS21.pdf" target="_blank" id="button_35873d1d8b5611a5c514ec3437e68163" class="btn btn-primary" data-mtop="0" data-mbottom="0">Full Paper (iros)</a>	
        <a href="/papers/LCSS2020.pdf" target="_blank" id="button_35873d1d8b5611a5c514ec3437e68163" class="btn btn-primary" data-mtop="0" data-mbottom="0">Full Paper (l-css)</a>	
        <a href="https://github.com/k1majd/CBF_TB_RRT" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Source Code</a></div>
        </div>
</div>
<br />
<br />
<div><iframe width="800" height="513" src="https://www.youtube.com/embed/c-yVyN7KvOE" title="Safe Navigation in Human Occupied Environments Using Sampling and Control Barrier Functions" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe></div>
<br />
<br />
</div>
  <div class="mb-5">
    <div class="text-3xl w-full font-bold">Publications</div>
  </div>
  <div class="row">
    <div class="column left">
      <span class="badge">IROS'21</span>
    </div>
    <div class="column right">
      <h3 class="font-semibold mb-0.2 text-justify">
        Safe Navigation in Human Occupied Environments Using Sampling and
        Control Barrier Functions
      </h3>
      <p class="font-light text-sm">
        <ins>K. Majd</ins>, S. Yaghoubi, T. Yamaguchi, B. Hoxha, D. Prokhorov,
        and G. Fainekos
      </p>
      <i class="font-light text-sm">
        IEEE/RSJ International Conference on Intelligent Robots and Systems
        (IROS), 2021.
      </i>
      <p class="my-2 text-justify"></p>
      <a href="/bib/iros21.txt">[BibTex]</a>
      <!-- <a href="/posters/poster_ICRA2022.png">[poster]</a> -->
    </div>
  </div>

  <br />
  <div class="row">
    <div class="column left">
      <span class="badge">L-CSS'20</span>
    </div>
    <div class="column right">
      <h3 class="font-semibold mb-0.2 text-justify">
        Risk-bounded Control using Stochastic Barrier Functions
      </h3>
      <p class="font-light text-sm">
        S. Yaghoubi, <ins>K. Majd</ins>, G. Fainekos, T. Yamaguchi, D.
        Prokhorov, and B. Hoxha
      </p>
      <i class="font-light text-sm"> IEEE Control Systems Letters.</i>
      <p class="my-2 text-justify"></p>
      <a href="/bib/lcss20.txt">[BibTex]</a>
      <!-- <a href="/posters/poster_ICRA2022.png">[poster]</a> -->
    </div>
  </div>