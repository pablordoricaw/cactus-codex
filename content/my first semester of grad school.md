---
title: My First Semester of Grad School 
---

My first semester in grad school left me with plenty of new concepts, ideas and thoughts in my head. I want to write about them to help me distill them, realize what questions I have unanswered, make new connections and have a record of this process. Where to begin 🤔?

Let me start with my classes. I took 4 classes and audited a 5th one - in that order:

- Natural Language Processing,
- Introduction to Databases,
- System-on-Chip Platforms,
- Heterogenous Computing for Signal and Data Processing, and
- Computer Architecture

I want to continue to some of my favorite ideas from my courses.

## An Exciting Time for Software, Algorithms and Computer Architecture

The key motivating idea for my SoC Platforms, Heterogenous Computing and Comp Arch classes was that there is an increasing demand for computational processing power spearheaded by AI that can't be met by performance improvements from continuing transistor miniaturization due to the slowing down of Moore's Law, and the end of Dennard Scaling in the early 2000s.

To meet this demand we'll need to look for performance enhancements elsewhere. The authors of the paper "[There's plenty of room at the Top: What will drive computer performance after Moore's law?](https://www.science.org/doi/10.1126/science.aam9744)" firmly believe the performance gains will need to come from software, algorithms and hardware architecture.

## The Elegance of GPUs

It was my first time writing software for GPUs, and one thing became clear. To write good software for GPUs, it is crucial to have a good understanding of the GPU architecture.

I found the foundational idea of the design of GPUs to be very elegant.

GPUs are SIMD engines under the hood that are programmed using threads instead of SIMD instructions. GPUs follow the Single Program Multiple Data programming model while following a SIMD execution model by grouping the threads executing the same instruction onto a warp(NVIDIA)/wavefront(AMD).

The warp/wavefront is essentially a SIMD operation formed by the hardware.

So in essence a GPU is a SIMT machine where multiple instruction streams of scalar instructions (threads) are dynamically grouped for execution.

Additionally, GPUs interleave the execution of the warps/wavefronts via warp-level fine-granined multithreading to tolarate long latency.

The HetSys Courses from [2022](https://www.youtube.com/watch?v=x1MA4MtO4Tc&list=PL5Q2soXY2Zi8J0QbZ0c9ERLdnFRnO5U8C&index=2&ab_channel=OnurMutluLectures) & [2023](https://www.youtube.com/playlist?list=PL5Q2soXY2Zi-qSKahS4ofaEwYl7_qp9mw)  available on YouTube taught by Dr. Juan Gomez Luna at ETH Zurich were an excellent resource to dive into the architecture of GPUs.

Unfortunately, I found the elegance of GPUs to not extend to programming them. Writing code for a single thread, while ensuring all threads properly operate on their corresponding data elements was tougher than expected.
