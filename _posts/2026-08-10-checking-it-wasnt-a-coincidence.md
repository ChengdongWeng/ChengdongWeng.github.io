---
title: "Checking that it wasn't a coincidence"
date: 2026-08-10
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

Before telling anyone about the upside-down U, I wanted more than one kind of evidence for it. One curve can look convincing by accident, especially with only 13 people.

The first check was about information. If averaging sensors helped because it threw away things that didn't matter, I should be able to measure how much it threw away. I compared each smaller picture with the original full-resolution one using normalized mutual information, which is roughly a score from 0 to 1 for how much of one picture you could work out from the other. At 4 by 8 the score was 0.17. About 83 percent of the information in the original picture was gone, and the best models lost only 2 to 3 points of macro-F1. Most of what the full mat records apparently has nothing to do with posture.

The second check was about confidence. A model gives a probability with every answer, and a well-behaved model that says it is 90 percent sure should be right about 90 percent of the time. The size of the gap between those two is called calibration error, or ECE. At full resolution the ResNet's ECE was 0.175, and in 7 of the 13 rounds it was above 0.1. At 10 by 21 it dropped to 0.018, about ten times smaller. So at full resolution the ResNet was not only wrong more often, it was also very sure of its wrong answers. That is what overfitting usually looks like.

The third check was for the models whose curves looked flat. I ran a statistical test for a break point, the place where a curve suddenly changes slope, and it found no evidence of one for the random forest, XGBoost or PointNet. I had to be careful with what that means. It doesn't prove there is no break point. It only says this data doesn't show one, so in my notes I wrote "no evidence of a breakpoint" and not "there is no breakpoint."

With three different signals pointing the same way, I felt ready to write it up. I put everything into a summary file, including a note about the 4,095 readings. By my count, 8 of the 13 people had readings stuck at that ceiling, probably where the hips and shoulders press hardest. I wrote it down as something that might support the second explanation, and as something any report would have to mention.

Then I wanted to save all of it properly. After losing the first run, this felt more urgent than any analysis. I committed the results and the analysis code to git and tagged that commit as v1, so I could always come back to exactly this state. While doing that I noticed something that scared me a little. The main results CSV was not in git at all. A rule in my ignore file, the file that tells git what to skip, had been quietly excluding it. The one file that would cost days of GPU time to regenerate was the one file that wasn't being saved. I added an exception for it and checked that git was really tracking it this time.

The last step was a backup somewhere other than my laptop. I made a private repository on GitHub and pushed everything to it. The push failed at first because git was still set to an old proxy port that I wasn't using anymore. Once I gave it the right port for that one command, it went through.

I also sent my mentor an update email with the main numbers. The next step was the experiment that could separate the two explanations.
