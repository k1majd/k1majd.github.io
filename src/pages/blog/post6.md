---
layout: "../../layouts/BlankLayout.astro"
title: "Safety-aware Expansion for Neural Network Repair"
description: "Inspired by the popular cascade-correlation algorithm, this project introduces a safety-aware growing neural network method aimed at expanding neural networks with new hidden units dedicated exclusively to responding to faulty samples."
pubDate: "Sep 5 2023"
heroImage: "/projects/nnreplayer_prosthesis/tumb8.jpg"
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
    <h2 style="text-align:center " id="center" class="text-4xl w-full font-bold ">Safety-aware Expansion for Neural Network Repair</h2>
  </div>
<div class="mb-5">
    <h2 style="text-align:center" id="center" class="font-light text-2xl w-full font-bold "><a
        href="https://k1majd.github.io"
        >K. Majd</a
      >, <a
        href="https://fainekos.net"
        >G. Fainekos</a
      >, and <a
        href="http://henibenamor.weebly.com"
        >H. Ben Amor</a
      ></h2>
  </div>

<div>
    <img
        src="/projects/nnreplayer_prosthesis/tumb9.jpg"
        alt="profile image"
    />
</div>
<br />
<div>
<div class="mb-10 text-justify">
    <b> Abstract:</b> 
     Deep Neural Networks (DNNs) have revolutionized robotics by enhancing autonomous perception and interaction. However, their application in safety-critical scenarios is constrained due to potential unsafe behavior with unseen data and the need to adapt to new safety requirements. Neural network repair methods aim to address these issues with existing approaches focusing on weight modification or architecture extension. Existing repair methods lack guaranteed safety, are computationally demanding, or degrade the network's original performance in the repaired regions. This paper proposes a novel repair method inspired by the cascade-correlation algorithm, utilizing neural network expansion to ensure safety and maintain original performance of the network. The proposed repair method involves the expansion of a neural network by introducing new hidden units into its last hidden layer. The training process for the added units utilizes gradient descent to maximize its covariance with constraint violation errors. The objective of this training is to ensure that the added neurons only activate in response to faulty samples. By doing so, the method aims to maintain the network's original performance for correct samples. After the isolation training of the newly added neurons, the last layer of the network undergoes fine-tuning with quadratic programming (QP). The QP-based fine-tuning ensures the satisfaction of constraints for the faulty samples. We showcase the effectiveness of our method in two applications: repairing a faulty classifier in the aircraft collision avoidance system and repairing a controller designed for a lower-leg prosthesis device.
  </div>
<br />
<br />
