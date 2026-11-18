---
title: "Turning notes into a paper"
date: 2026-09-20
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

I spent most of this week rebuilding the draft. The experiments and figures stayed, but almost every sentence around them had to change.

I started with the structure, because it was the part with a clear answer. I looked at how papers in the journals I was considering were organized and followed the same layout: Introduction, Related Work, Materials and Methods, Results, Discussion and Conclusions. Then I moved the two pieces my mentor had pointed out. The paragraph about testing only on people the model never trained on went into Methods, since it describes how the evaluation works. The list of what this study contributes went into the Discussion, after the results it depends on.

Turning bullet points into paragraphs was slower than I expected. A bullet point lets you skip the connection between two facts. A paragraph doesn't, so I kept going back to the results to check exactly what was being compared before I could write the sentence that linked them.

References took the longest. The first draft had none, so I went back through the papers I had read since July and matched each claim to a paper that supports it. The draft now has 32 references. I've checked 8 of them against the PDFs I have. The other 24 still need to be checked one at a time for page numbers, journal names and years.

While writing the Related Work section I found something that worried me. A 2024 paper by Wu and others in IEEE Transactions on Neural Systems and Rehabilitation Engineering says that the size of a mat and the density of its sensors are two separate factors, and that extra sensors can add redundant information that might even hurt. That is very close to what I thought was the new part of my project. For a while I thought the whole idea had already been done.

After reading those sections more carefully, I think the difference is real but smaller than I had been telling myself. As far as I can tell, they didn't change the two factors independently on one public dataset, and they didn't compare several kinds of models while keeping every test person out of training. So what I can claim is narrower: this study separates the two factors and tests both of them under stricter conditions. I wrote it that way, cited their paper in Related Work and in the Discussion, and explained the difference. I still need to read it from start to finish to be sure exactly what they changed.

The draft has every section now, but it is full of red notes. The training details section is empty, because I want to copy the exact settings from my code instead of writing them from memory. A table with every model's score at every resolution is still missing. Some figures have Chinese axis labels from when I made them only for myself, and their titles sound like my notes, things like "CNNs collapse." Those need to be redone in plain, neutral wording.

The language is the part I'm least happy with. Some paragraphs read like a paper now, and others still read like my notes with periods added. I'll keep working through them one section at a time this week.
