---
layout: post
title:  "The halting problem"
date:   2017-08-13 17:00:00 +0800
categories: maths
---
There's no shortage of material on the Internet on the topic. [Wikipedia](https://en.wikipedia.org/wiki/Halting_problem) does a reasonable job, and remains a wholesome reference. I'm simplifying the proof as a quick reference.

Imagine we have a magical, constant-time algorithm that can decide whether a program will halt on its input, like so:

```python
def will_halt(program, input):
  if program(input) will halt:
    return True;
  else:
    return False;
```

Then, I build my devil program to turn things upside down:

```python
def devil(program):
  if will_halt(program, program):
    while True: continue;
  else:
    return;
```

Here comes to proof. What happens when I call devil with itself as argument, as in `devil(devil)`?

Calling `devil(devil)` is exactly the same as `program(input)` in `will_halt`, so if `will_halt` is true (line 2 in `devil`), `devil` loops forever and will not halt. If `devil(devil)` does not halt, then `will_halt` is false, and `devil` returns and halts (else-branch in `devil`). Either case, `devil` defies our magical `will_halt` and we have a contradiction.

By [reductio ad absurdum](https://en.wikipedia.org/wiki/Reductio_ad_absurdum), this means our initial premise of the existence of `will_halt` is false. In other words, there exists no algorithm that can decide whether a program halts on its input.

P.S. I consider returning boolean literals in an if-else block an anti-pattern, and am doing it here only for clarity.

