---
layout: page
title: About
permalink: /about/
---

I was reading Richard Feynman's report to the space shuttle Challenger inquiry about the same time I thought of starting a software journal, and it struck me deeply how certain aspects of NASA's failures mirror those of typical non-agile software projects.

Feynman discussed how ordinary military and civilian aircraft engines are designed bottom-up, where properties and limitations of materials used are understood, larger components are designed and tested individually. Deficiencies are rectified at this level when it's still cheap to do so. The entire engine is assembled to specification and any flaw can be easily isolated and fixed because all those design limits and tests are well-understood. The result is that engines thus designed are generally successful.

In contrast, the space shuttle main engine was handled in a top-down manner. The whole engine was designed and put together all at once with "relatively little detailed preliminary study of the material and components." When there were defects found with the such components as bearings and blades, engineers were left to figure out the cause amid a multitude of possibilities such as temperature, speed, pressure, vibration, etc. The result is that there wasn't a complete understanding of the root cause and by inference the engine design cannot be reasoned about and trusted with high level of confidence.

At this point I'm reminded of writing software using TDD vs the tragically-common test-as-a-blackbox via the UI approach. With TDD, you gain understanding and confidence of each component as you go along. With manual UI testing, you lose the ability to reason about the cause of failure. Just as NASA managers had gradually and subtly altered the safety criteria so that flights may still be certified in time, software is often released by project managers at the eleventh hour with little regard to safety.

The software I write will never be as mission-critical as that on the space shuttle, but I'm using the lessons learnt from the Challenger disaster to remind myself the importance of getting good at one's craft.

