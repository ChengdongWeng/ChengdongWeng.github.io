---
title: "Starting from zero"
date: 2026-07-16
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

I had a new plan and nothing to run it on. I was still a bit upset about radar, but sitting around wasn't going to help, so I spent a whole evening setting up.

The first choice was where to run the code. Google Colab needs no installation and gives you free GPU time, which sounded nice. But this project was going to last months, I would be running the same code again and again, and I didn't want my work to depend on a browser tab that times out. I chose my own laptop.

I was sure I had installed Anaconda before. I opened the Anaconda website, saw "Welcome back," and took that as proof. It wasn't. That page only meant I had an account. It said nothing about what was on my laptop. The real test was one line in the command prompt:

```
conda --version
```

It came back with "'conda' is not recognized." For a minute I thought I had to reinstall everything. Then I typed "anaconda" into the Start menu and found Anaconda Prompt, Navigator, the whole set. I had installed it at some point, but it wasn't on the system PATH, so the normal command prompt couldn't find it. From then on I only used Anaconda Prompt.

Next I made an environment just for this project, called `posture`, with Python 3.11:

```
conda create -n posture python=3.11
conda activate posture
```

An environment keeps this project's libraries separate from everything else on my laptop, like my VEX code. Inside it I installed NumPy, matplotlib, SciPy, scikit-learn, pandas, Jupyter, a couple of smaller tools, and PyTorch. I picked the CPU-only version of PyTorch even though my laptop has an NVIDIA GPU, because I didn't want to deal with GPU drivers on the first night. I could always switch later if I needed it.

The final check printed what I wanted to see:

```
all good
2.2.2
```

Above it, though, was a block of red text: `Failed to initialize NumPy: _ARRAY_API not found`. The program still ran, so my first instinct was to move on. The problem was that conda had given me NumPy 2.4.6, while the PyTorch build I had was made for NumPy 1.x. The two mostly work together, until you pass data from one to the other, and training does that all the time.

My first fix, `conda install "numpy<2"`, didn't do anything. Conda decided nothing needed to change, and the warning came back. Asking for an exact version worked:

```
conda install numpy=1.26.4 -y
```

After that the output was clean. I made a note to myself to read warnings even when the code runs.

Then came the project folder: `C:\research documents\sleep-posture-resolution`, with four folders inside called `data`, `notebooks`, `src` and `results`. It's the most boring part of this post, but every file in the project was going to go into one of those four folders, so I wanted them set up properly. I also lost some time here going back and forth between File Explorer and the command line, and at one point I wasn't even sure where I was supposed to press Ctrl+V.

To check that everything worked together, I opened Jupyter and drew a fake pressure map, just a 32 by 64 grid of random numbers:

```python
import numpy as np
import matplotlib.pyplot as plt

np.random.seed(42)
fake_pressure = np.random.rand(32, 64)
plt.imshow(fake_pressure, cmap='hot')
plt.colorbar()
plt.show()
```

It looked like static on an old TV, nothing like a person. I was still happier than I should have been, because it meant Python, NumPy, matplotlib and Jupyter were all working together.

The last thing that night was the data. I started with PMD, the Pressure Map Dataset on PhysioNet, where 13 people lay in 17 postures on a mat with 2,048 sensors. It's only about 102 MB, so it downloaded fast. The folder had a very long name, so I renamed it to `pmd`.

Inside `experiment-i` there is one folder per person, S1 to S13, and each one has files `1.txt` to `17.txt`, one per posture. At first I couldn't even tell they were text files, because Windows hides file extensions by default. Each line in a file is one frame, one second of recording, with 2,048 numbers separated by tabs. S1's `1.txt` has 82 lines, so 82 seconds of one person lying still.

My note for the next step was to fold each line into 32 rows of 64 numbers and draw it.

By then it was late. I still hadn't drawn a single real pressure map, and that would have to wait.

