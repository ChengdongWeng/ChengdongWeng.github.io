---
title: "My notes said thirty"
date: 2026-08-28
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

With SLP on hold, PoPu was next. Before running anything, I wanted to check my notes about it against the actual files. I had just spent several days finding out that my SLP notes were wrong in more than one place, so I didn't want to trust anything I hadn't looked at myself.

My notes said two things about PoPu. Each recording had about 30 snapshots, and the repeated snapshots were already being handled in my loader. I wrote a short script that only reads and prints: folder names, file names, the keys inside each file and how many snapshots each one has. It doesn't change anything, so it can't break anything.

Both notes were wrong. Each volunteer has 86 files, one per recording plus a couple of empty-bed files, and each file holds 10 snapshots, not 30. The 30 frames per volunteer and posture I counted in July come from 3 recordings of each posture with 10 snapshots each. Then I searched my code for anything that removed repeated snapshots, and nothing came up. The loader was stacking all 10 snapshots of every recording straight into the data.

That matters because the 10 snapshots in one recording are taken a few seconds apart while the person lies still. I compared them, and the differences were under 0.07, which is about the size of sensor noise. So they aren't 10 samples. They're one sample counted ten times. Since all of a volunteer's recordings stay in the same fold, this wouldn't put a test person into training. But it would make the dataset look about ten times bigger than it is: around 50,400 frames, when there are really about 5,040 recordings. Every pose would show up ten times in training and count ten times in the test score. Any statistics I ran later would also treat near-copies as if they were separate evidence.

There were two ways to fix it. I could average the 10 snapshots into one frame, or I could keep just one of them. Averaging sounds better at first, because it removes noise. I went with keeping one, the middle snapshot, number 5 if you count from 0. The whole reason I'm using PoPu is to compare it with PMD, and PMD gives single frames, not averages. If PoPu got averaged frames, its pictures would be cleaner than PMD's, and PoPu might look more robust for a reason that has nothing to do with the mat. For this project, keeping the datasets comparable matters more than making one of them look as good as possible.

I picked the middle one instead of the first one for a simple reason. The first snapshot is sometimes taken while the person is still settling into the pose, and in my check it was the one that differed most from the rest. The middle one is the safest choice.

I added this as an option in the loader instead of changing the old code, and checked that it really cut the data from 10 to 1 per recording. Then I ran a small test: one fold, the random forest and the small CNN, four classes including face-down. The random forest got 0.921 accuracy and the small CNN got 0.956. Those aren't suspiciously perfect and they aren't near chance, which for four classes is 0.25. PoPu was finally running.

That made two sets of notes in one week that didn't match the real files. Both times I only found out because I ran a script that just reads and prints before running anything else. I'm going to keep doing that first.
