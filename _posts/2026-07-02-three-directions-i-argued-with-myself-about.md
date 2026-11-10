---
title: "Three directions I argued with myself about"
date: 2026-07-04
categories: blog
tags: research
toc: false
header:
  teaser: /assets/images/default-teaser.jpg
---

At the start of July I had a mentor, about six months, and an idea I was really excited about: a cheap sleep monitor built around a millimeter-wave radar. A small sensor sits next to the bed, and without touching you at all, it can tell how you're lying and how you're breathing. Before our first proper meeting, my mentor asked me one thing. What's actually new about it?

I didn't have a good answer yet, so I spent the first days of July reading.

**Why radar in the first place**

Before I could pick a direction, I had to be sure radar was even the right sensor. There are a lot of ways to watch someone sleep, and every one of them gives something up.

A camera is the obvious choice. It sees posture directly, and computers are very good with images now. But it's a camera, pointed at you, in your bedroom, all night. I wouldn't want that, and I don't think most people would either. It also struggles in the dark unless you add infrared, and a blanket hides most of what it's trying to see.

Wearables are the other big group. A chest strap measures breathing well, and lots of people already own a smartwatch. The catch is that you have to wear them. A strap around your chest isn't comfortable to sleep in, and a watch only feels your wrist, so it has to guess what the rest of your body is doing.

Then there's the hospital version, a sleep study called polysomnography. It's the gold standard, but it means a night in a lab with sensors and wires attached all over you. Nobody does that every night at home.

Pressure mats go under the sheet and measure how your body presses into the bed. You don't wear anything and there's no picture of you. I looked at them too, but the good ones have thousands of sensors and cost a lot, and they only feel what's touching the bed.

Radar seemed to get around most of these problems at once. It doesn't touch you. It doesn't make an image, so there's never a picture of your face or body anywhere, which matters a lot for something that sits in a bedroom. It works in the dark and through a blanket. And since it can pick up chest movements of a few millimeters, one sensor could in principle track breathing as well as posture.

It wasn't perfect, and I could already see some of the problems. The raw signal is hard to make sense of. Another person or a pet in the room adds noise. And there's a lot less public radar data out there than image data. But on paper it was the only sensor that checked every box I cared about. I'll admit it also just sounded cool.

**Directions considered**

The more I read, the more my one idea split into three, and I went back and forth between them for days.

**A. Does it still work on someone new?** In a lot of the papers, recordings from the same person end up in both the training data and the test data. That makes the numbers look better than they would be for a stranger. Direction A was to test properly on people the model had never seen, ideally over real nights of sleep. The overnight part was the problem, because I had no way to run overnight recordings. Then I found a preprint from about a week earlier doing something pretty close to the cross-person part, which was not fun to discover. A on its own suddenly looked a lot less new.

**B. Can it be cheap?** Research radars are expensive, but you can buy a consumer 60 GHz radar module for around a hundred dollars. Direction B was to use one of those with a small model and see how close it could get to a research setup. I liked that anyone could understand why that matters. What I didn't like was that the cheap radar was the whole project, so I'd be buying hardware before knowing whether its signal was even good enough.

**C. Posture and breathing together.** For a lot of people with sleep apnea, lying on their back makes it worse. In theory one radar could see both the posture and the pauses in breathing. This was the one I wanted most, because it's the one that could actually matter to someone. It was also the one I could least do. To know when a person really stops breathing, you need polysomnography, and I couldn't find a public dataset with clean labels for both posture and apnea. My parents don't run a hospital, so collecting that kind of data myself was out too.

Then I looked at what I actually had. A fixed budget, a space where I could record, and no realistic way to get more than about twenty people. I also wanted real hardware in the project, not only code.

So I ended up combining A and B. Train a model on a public dataset recorded with a research radar, then test it two ways: on people it had never seen, and on recordings from a cheap radar I'd set up myself. If the hardware part went badly, I could fall back to A alone, and that would still be a real result. C went into future work, which felt a bit like giving up on the part I cared about most, but I couldn't see another way.

Writing all of this out side by side helped more than thinking about it in my head. Every option had something I wanted and something I couldn't get around. Once I could see that on one page, the question stopped being which idea sounded best and became which one I could actually finish.

That was the plan I took into getting ready for the meeting.
