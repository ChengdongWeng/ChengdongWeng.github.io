---
title: "Getting ready to defend an idea"
date: 2026-07-15
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

The meeting with my mentor was on July 16. The day before, I had my plan, A and B combined, and I needed to turn it into something he could read and poke holes in. I was nervous. I'd never had to defend a research idea to someone who does research for a living.

He'd asked for two things, so I wrote two documents. One was the research question and protocol: what I wanted to find out, what data I'd use, and how I'd evaluate it. The other was a study outline with a timeline. Both went through a lot of drafts. I cut direction C out completely instead of leaving half a section about it, made both documents shorter, and wrote the limits in plainly: at most 15 adult participants, short recording sessions, nothing overnight and nothing medical. Then I sent them with a short email so he'd have time to read them first.

Next was the paper he'd sent me, a 2021 review of millimeter-wave radar for contactless sleep monitoring. I went through it section by section, pretty slowly, and spent the most time on the part about open challenges, since that was the part he'd quoted to me. The section on posture surprised me. The review only covered two studies on radar-based sleep posture, and one of them reported 100% accuracy.

My first reaction was something close to panic. If someone already got 100%, what was left for me to do? Then I read how they got it. Three classes, a small number of people, a hand-written rule instead of a trained model, and no testing on anyone new. A number like that doesn't mean the problem is solved. It means nobody had checked it properly, and checking it properly was more or less what direction A was about. I went from worried to a little bit excited in about ten minutes.

After that I tried to guess what he'd ask me. I ended up with ten questions and wrote an answer to each. Some were obvious, like "someone already got 100%, so why bother?" Others were harder, like whether the dataset I wanted to use even had posture labels I could trust. My honest answer to that one was that I didn't know yet, so I listed some backup datasets in case it didn't.

I was pretty sure he'd also ask how I would avoid the same mistakes I was pointing out in other papers. So I wrote down four rules for my own evaluation:

1. The same person is never in both the training data and the test data.
2. The test set gets used once, at the very end, after all the tuning is done.
3. Every result is run with at least three random seeds and reported as an average with its spread, not the best run.
4. Every model is compared against simple baselines, so I can show it's actually adding something.

The last thing was a plan for the meeting itself. Start with the overall structure, not the details. Show the fallback, so it's clear the project still works even if the hardware doesn't. Hand him my open questions and let him steer. Then stop talking and listen. I wrote that last step down on purpose, because I knew I'd want to keep explaining.

I went to bed feeling about as ready as I could be. Almost none of the radar plan survived the next day. The four rules did, though, and I still check everything in this project against them.
