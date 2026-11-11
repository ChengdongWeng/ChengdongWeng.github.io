---
title: "Cleaning up a notebook that got out of hand"
date: 2026-07-31
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

By the end of the week my notebook was a mess. It had grown one cell at a time for two weeks: loaders, plots, label maps, five kinds of models, training loops, a few things I had tried and abandoned. It worked as long as I ran every cell in exactly the right order. When I didn't, it broke.

The cell that finally made me deal with it was the one meant to check all seven models at once. It had never run all the way through. This time it failed with a NameError saying BaselineCNN wasn't defined. The model was defined in the notebook, just in a cell further down, and Jupyter only knows about cells you've already run.

Fixing that one error would have taken a minute. But while I was looking for it, I found worse things. The dictionary that maps the 17 PMD postures to 3 classes was defined twice, first as a placeholder and then as the real version. The function that builds the training data existed in an old version that couldn't shrink the mat and a newer one that could. PointNet was defined three separate times. Whichever version ran last was the one that counted, and I couldn't always tell which one that was.

I had two options. I could reorder the cells and move on, or I could move everything into proper Python files and import them. The second option would take most of a day. I chose it anyway, because the whole project depends on running the same code hundreds of times, and I didn't want any result to depend on which cells I happened to run that morning.

The new structure is a folder called src with one file per job. One file holds the paths, one loads PMD and PoPu, one reads the frozen splits, one shrinks the mat, one builds the training data, one does the training, and there's a separate file for each neural network. For every function that had more than one version, I kept only the newest working one and threw the rest away.

I built the files one at a time, and after each one I tested that it imported without errors before starting the next. That sounds slow, but it meant that when something broke, I knew exactly which file did it. Windows caused the most annoying problem. A file I named config.py in Notepad was quietly saved as config.py.txt, because file extensions were hidden, so Python couldn't find it. Once I knew to look for that, it was easy to fix.

Then I ran the check on all seven models again, using one PMD split, one seed and a short training run. For the first time, every model finished and gave a number. They weren't real results. The ResNet stopped after six epochs because the quick test only waited three epochs for improvement. But everything ran from start to finish in one go.

The last step was a script to run the whole first experiment by itself: seven models, six resolutions, 13 PMD splits and 3 seeds, which comes to 1,638 runs. It writes each run to a CSV file as soon as that run finishes, so if anything stops halfway, it can pick up where it left off instead of starting over.

The first launch didn't get far before two more bugs showed up. XGBoost crashed because the same setting was being passed to it twice. BaselineCNN crashed only at the two smallest mat sizes. It shrinks the image by half three times, and at 5 by 10 or 4 by 8 there is nothing left to shrink by the third time. I changed it to skip that step when the image is already too small. The results file had 98 rows by then, 20 of them failures, so I deleted it and started the full run again from zero.

This time it kept going.
