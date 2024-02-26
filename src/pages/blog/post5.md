---
layout: "../../layouts/BlankLayout.astro"
title: "Safety-aware Neural Network Repair for Robotic Systems with
Predictive Models"
description: "This project presents a two-step supervised learning approach for
safety-aware robot learning, using predictive models to enforce explicit and implicit contraints on the policy."
pubDate: "June 5 2023"
heroImage: "/projects/nnreplayer_prosthesis/github_demo3.gif"
badge: "Under Review"
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
    <h2 style="text-align:center " id="center" class="text-4xl w-full font-bold ">Safety-aware Neural Network Repair for Robotic Systems with Predictive Models</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold "><a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, G. Clark, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      >, and <a
        href="http://henibenamor.weebly.com"
        >H. Ben Amor</a
      ></h2>
  </div>
<div>
    <img
        src="/projects/nnreplayer_prosthesis/github_demo2.gif"
        alt="profile image"
    />
</div>
<br />
<div>
<div class="mb-10 text-justify">
    <b> Abstract:</b> 
     We introduce a novel approach for safety-aware robot learning, focusing on policy repair using predictive models. 
      The proposed method combines behavioral cloning with neural network repair in a two-step supervised learning framework. 
      In the first step, a policy is learned from expert demonstrations, while the second step utilizes a predictive model to impose safety constraints on the policy. 
      The incorporation of predictive models eliminates the need for repeated interaction with the robot, saving time on lengthy simulations typically required in reinforcement learning. 
      The predictive models can encompass various aspects relevant to robot learning applications, such as proprioceptive states and collision likelihood. 
      Our method is showcased in two applications: (i) mobile robot navigation, and (ii) a real-world lower-leg prostheses.
      Our experimental results demonstrate that the learned policy successfully adheres to a predefined set of safety constraints.
      Additionally, we have shown that our method effectively reduces the need for repeated interaction with the robot, leading to substantial time savings during the learning process.
  </div>
<div class=" col-xs-12 col-sm-2 ">
<div class="center">
    <div id="col_inner_id-638fba18b86c0" class="fw-col-inner" data-paddings="0px 0px 0px 0px">	
        <a href="https://github.com/k1majd/SARP?tab=readme-ov-file" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Source Code</a>
        </div>
</div>
<br />
<br />
