---
layout: post
title:  "Programming block out period on Sanden heat pump"
date:   2023-02-14 18:00:00 +1100
categories: note-to-self
---

# Why block out?
The Sanden HWS heat pump automatically starts at 10am (or 11am summer time). However, it also 
starts early morning if it thinks you may not have enough hot water for morning shower. This is nice, 
but costs money buying electricity when solar panels aren't producing. Block out prevents the heat pump from 
working during those hours.

# Steps

- Open 4 screws on top of the heat pump, remove the top lid.
- Remove the centre screw that holds the control panel in place.
- Using the control panel, press enter once. The LCD now shows the heat pump's clock. Make sure it's correct.
- Press and hold both arrows until LCD flashes.
- Press up to find 'bo'. Enter.
- To block the heat pump from 9pm to 9am, set bo value to `2109`. Press enter to set.

To disable block out, set bo value to `0000`.

[user manual](/assets/gaua45hpa.pdf)

