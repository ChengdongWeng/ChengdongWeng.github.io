---
title: "The first real pressure map"
date: 2026-07-25
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

After the fake heatmap and the dataset hunt, it was finally time to look at real data. I opened the first file, subject 1 in posture 1, and loaded it.

The first thing I printed was the range of the numbers. The dataset's page said readings went from 0 to 1000. The largest value in this one file was 3,841. It was a small thing and I moved on quickly, but I made a note that the data and its description didn't quite agree.

Then I turned one frame into a picture. Each line in the file has 2,048 numbers, and my notes from setup night said to fold them into 32 rows of 64. I didn't know which way the body ran, so I plotted the frame twice: once as it came out, 32 by 64, and once flipped on its side, 64 by 32.

The flipped version looked like a person, or at least I thought it did. I could see a bright area at the top, a bigger one in the middle and another one lower down, which I read as head and shoulders, torso and hips. The other version was stranger. It looked like two bodies lying side by side.

That was a bit strange. The explanation I went with was symmetry. This was someone lying on their back, so the left and right halves of the body press into the mat in almost the same way, and that could make the picture look doubled. It sounded reasonable, the flipped version looked fine, and I wanted to get on with the project.

I also averaged all the frames of the recording into one picture, plus a second picture showing every sensor that was ever touched. Those looked more like an outline of a body, which made me even more confident that the data was being read correctly.

Before moving on, I wrote down a rule so I wouldn't confuse myself later. Inside the code, every frame stays as 32 by 64. I only flip it when I'm showing it on screen. Later code would shrink the mat along one direction or the other, and I didn't want to lose track of which direction was which. There was also a smaller fix that day. Every Chinese title on my plots showed up as empty boxes, because matplotlib couldn't find a Chinese font, so I set it to use one that comes with Windows.

With one file loading correctly, the next job was to stop looking at a single recording and read all thirteen people.
