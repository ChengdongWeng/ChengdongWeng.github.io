---
title: "Looking for a hundred people"
date: 2026-07-21
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

Once PMD was on my laptop, one number started bothering me. Thirteen. The whole dataset was thirteen people. If the point of the project was to say something about how people lie in bed, thirteen felt like a joke. I decided I wanted at least a hundred.

So before going to bed, I went looking.

It didn't take long to see the whole field, because there isn't much of it. PMD has 13 people. A dataset from Georgia Tech has 17. PoPu, which I had already noticed because it records on two mats at once, has 60. SLP, from a lab at Northeastern, has 109. That was it. SLP was the only real dataset with more than a hundred people, and you have to apply for it.

There were bigger ones, but they weren't real. One synthetic dataset has almost a hundred thousand pressure maps, made by simulating bodies lying on a mat with a physics engine. That sounds great until you remember that no actual person ever lay on that mat. If my result only held on simulated people, I wouldn't trust it, and I doubt my mentor would either.

My honest reaction was something like: there are eight billion people on this planet, and this is all we have? It made more sense once I thought about what it takes to build one of these datasets. You need a mat that costs thousands of dollars, ethics approval, a lab, and a lot of people willing to lie down in a dozen positions while someone records them. Not many groups do that, and even fewer release the data.

Then I had what I thought was a clever idea. If there's no single big dataset, just put the small ones together. 13 plus 17 plus 60 plus 109 is almost two hundred people.

It doesn't work that way. Every dataset uses a different mat. PMD's mat has 2,048 sensors in one grid. PoPu's top mat has 1,728 in a different grid, and its readings are on a different scale. Throwing them into one pile is like mixing temperatures in Celsius and Fahrenheit and asking a model to learn from the numbers. It might mostly learn which mat each frame came from.

What changed my mind was noticing that this difference between mats wasn't really a problem for my project. It was part of the question. Layer two of my plan was to check whether an answer from one mat still holds on another. For that, you don't merge datasets. You run the same experiment on each one separately and compare. So more datasets did help, just not in the way I first wanted.

I also found out that several of the papers closest to my topic used PMD's 13 people and nothing else. That made me think about what actually makes a result believable. A hundred people tested carelessly is worse than thirteen people tested properly, where the model never sees the person it's tested on. The headcount I was so worried about mattered less than how the testing was done.

There was one more small lesson that night. PoPu offers a few versions to download, and my first instinct was to grab the biggest one. The biggest one just adds body-segmentation maps that I didn't need. The pressure data is the same in both. Taking the smaller one meant less to download and less to deal with in the code. Knowing what you actually need is a skill of its own.

So the plan became: use PMD first to get the whole pipeline working, then PoPu for the main comparison, and maybe SLP later as a third check. It was a much smaller pile of people than I'd wanted, but it was a plan I could start on right away.
