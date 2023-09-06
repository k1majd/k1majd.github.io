---
layout: "../../layouts/BlankLayout.astro"
title: "Joint Communication and Motion Planning for Cobots"
description: "This project unifies communication and motion planning to enrich human-robot interaction, to prevent potential deadlocks and freezing situations, and to maintain the planning efficiency in terms of raveled distances."
pubDate: "Mar 2 2022"
heroImage: "/projects/nnreplayer_prosthesis/tumb5.png"
badge: "ICRA'21"
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
    <h2 style="text-align:center " id="center" class="text-4xl w-full font-bold ">Joint Communication and Motion Planning for Cobots</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold "><a
        href="https://www.mdadvar.net/home"
        >M. Dadvar</a
      >, <a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, <a 
        href="https://www.linkedin.com/in/elena-oikonomou/"
        >E. Oikonomou</a
      >, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      >, <a
        href="http://siddharthsrivastava.net"
        >S.
        Srivastava</a
      ></h2>
  </div>
<div>
    <img
        src="/projects/nnreplayer_prosthesis/tumb4.jpg"
        alt="profile image"
    />
</div>
<br />
<div>
<div class="mb-10 text-justify">
    <b> Abstract:</b> 
     The increasing deployment of robots in co-working scenarios with humans has revealed complex safety and efficiency challenges in the computation of the robot behavior. Movement among humans is one of the most fundamental and yet critical problems in this frontier. While several approaches have addressed this problem from a purely navigational point of view, the absence of a unified paradigm for communicating with humans limits their ability to prevent deadlocks and compute feasible solutions. This paper presents a joint communication and motion planning framework that selects from an arbitrary input set of robot’s communication signals while computing robot motion plans. It models a human co-worker’s imperfect perception of these communications using a noisy sensor model and facilitates the specification of a variety of social/workplace compliance priorities with a flexible cost function. Theoretical results and simulator-based empirical evaluations show that our approach efficiently computes motion plans and communication strategies that reduce conflicts between agents and resolve potential deadlocks. 
  </div>
<div class=" col-xs-12 col-sm-2 ">
<div class="center">
    <div id="col_inner_id-638fba18b86c0" class="fw-col-inner" data-paddings="0px 0px 0px 0px">
		<a href="https://arxiv.org/pdf/2109.14004.pdf" target="_blank" id="button_35873d1d8b5611a5c514ec3437e68163" class="btn btn-primary" data-mtop="0" data-mbottom="0">Full Paper (icra)</a>
    <a href="https://www.youtube.com/watch?v=rFjrwiD0pSE&t=4s" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Talk</a>
    <a href="/posters/poster_ICRA2022.png" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Poster</a>
    </div>
</div>
</div>
<br />
<br />
</div>
  <div class="mb-5">
    <div class="text-3xl w-full font-bold">Publications</div>
  </div>
  <div class="row">
    <div class="column left">
      <span class="badge">ICRA'21</span>
    </div>
    <div class="column right">
      <h3 class="font-semibold mb-0.2 text-justify">
        Joint Communication and Motion Planning for Cobots
      </h3>
      <p class="font-light text-sm">
        M. Dadvar, <ins>K. Majd</ins>, E. Oikonomou, G. Fainekos, and S.
        Srivastava
      </p>
      <i class="font-light text-sm">
        IEEE International Conference on Robotics and Automation (ICRA), 2021.
      </i>
      <p class="my-2 text-justify"></p>
      <a href="/bib/icra22.txt">[BibTex]</a>
    </div>
  </div>