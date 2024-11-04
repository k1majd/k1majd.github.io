---
layout: "../../layouts/BlankLayout.astro"
title: "Safety-aware Neural Network Repair for Robotic Systems with
Predictive Models"
description: "This project presents a two-step supervised learning approach for
safety-aware robot learning, using predictive models to enforce explicit and implicit contraints on the policy."
pubDate: "June 5 2023"
heroImage: "/projects/nnreplayer_prosthesis/github_demo3.gif"
badge: "IROS'2024"
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
     This work introduces a new method for safety-aware robot learning, focusing on repairing policies using predictive models. Our method combines behavioral cloning with neural network repair in a two-step supervised learning framework. It first learns a policy from expert demonstrations and then applies repair subject to predictive models to enforce safety constraints. The predictive models can encompass various aspects relevant to robot learning applications, such as proprioceptive states and collision likelihood. Our experimental results demonstrate that the learned policy successfully adheres to a predefined set of safety constraints on two applications: mobile robot navigation, and real-world lower-leg prostheses. Additionally, we have shown that our method effectively reduces repeated interaction with the robot, leading to substantial time savings during the learning process.
  </div>
<div class=" col-xs-12 col-sm-2 ">
<div class="center">
    <div id="col_inner_id-638fba18b86c0" class="fw-col-inner" data-paddings="0px 0px 0px 0px">	
        <a href="https://github.com/k1majd/SARP?tab=readme-ov-file" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Source Code</a>
        <a href="/papers/IROS24.pdf" target="_blank" id="button_35873d1d8b5611a5c514ec3437e68163" class="btn btn-primary" data-mtop="0" data-mbottom="0">Full Paper (IROS)</a>	
        <a href="https://arizonastateu-my.sharepoint.com/:v:/g/personal/kmajd1_sundevils_asu_edu/EUdRXZcFhrNEq0oessmyRAEB1PG_mSYDxWjJrI63wwsNcg?e=PZQss9&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D" target="_blank" id="button_c260602177e94629b947d73881f0eb0a" class="btn btn-primary" data-mtop="0" data-mbottom="0">Talk (IROS)</a>
        </div>
</div>
<br />
<br />
