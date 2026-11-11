---
title: "Seven models and a GPU I didn't know I had"
date: 2026-07-29
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

My mentor's plan said to train a CNN at full resolution as the baseline. I wanted more than one model. If I only used one, and its accuracy dropped when I shrank the mat, I wouldn't know whether the mat had lost the information or just that one model had trouble with it. If several very different models all struggle at the same resolution, the problem is much more likely to be in the data.

So the plan became a set of models that look at a pressure map in very different ways, roughly from simplest to most complicated:

1. **Three classical models**: a linear SVM, a random forest and XGBoost. They flatten the map into one long list of numbers and know nothing about which sensors are next to each other. They're fast, and they answer a basic question: do I even need deep learning for this?
2. **A small CNN**, about 30,000 parameters. It looks at small patches of the map and builds up from there.
3. **A ResNet with squeeze-and-excitation blocks**, about 313,000 parameters. It's deeper, and it can learn which of its internal features matter more.
4. **A CNN with a Transformer on top**, about 869,000 parameters. The attention part lets every region of the mat look at every other region.
5. **PointNet**, about 76,000 parameters. It doesn't see a grid at all. Each sensor becomes a point with an x position, a y position and a pressure value. Because of that it doesn't care how big the grid is, so it fits the question of how many sensors you need better than any of the others.

PointNet was the one I had to think about, because it meant extra work: writing a model that's quite different from the rest and training it on every setting. I decided to do it. It's the model that's closest to the real question.

Then I did the math on training time, and it was bad. Every model at every resolution needs 13 rounds on PMD and 5 on PoPu, each with several seeds. On my laptop's CPU, the whole plan would take more than a hundred days.

I assumed my laptop didn't have a proper graphics card, or that it was switched off somehow, because I only ever use it for schoolwork. It turned out Windows could already see an NVIDIA RTX 4060 with 8 GB of memory. The problem was me. On setup night I had installed the CPU-only version of PyTorch on purpose, and that version simply ignores the GPU.

Fixing it meant uninstalling PyTorch and installing the CUDA version, which is about a 2.5 GB download. Before that, I ran a command that shows what the graphics card is doing, and it listed more than seventy background programs using a bit of GPU memory, including WeChat, a music app and several browser windows. They only took about 0.8 GB, so I left them alone.

The first real test went badly. The moment I moved a model onto the GPU, the Jupyter kernel died. No error message, it just stopped. I tested the same thing from the command line and it worked fine, so the GPU and PyTorch were okay and the problem was Jupyter. Restarting the whole Jupyter server, not just the kernel, fixed it.

After that, the small CNN processed about 11,000 frames per second, roughly 40 times faster than before. One pass over the PMD training data took about a second and a half. The estimate for the full set of experiments went from more than a hundred days to about six.

Six days was still a lot, but it was something I could plan around.
