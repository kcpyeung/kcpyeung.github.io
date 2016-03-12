---
layout: post
title:  "correct horse battery staple"
date:   2016-02-14 21:37:36 +0800
categories: security
---
Many are familiar with this xkcd comic:

![xkcd](https://imgs.xkcd.com/comics/password_strength.png)

Not many understand *why* random dictionary words can be more secure than leet passwords.

[Diceware](http://world.std.com/~reinhold/diceware.html) is one way you can use to generate secure passphrase from random dictionary words. The diceware word list has 7,776 words, from the fact that you throw a die 5 times, ie, 6<sup>5</sup> = 7,776. A six-word passphrase therefore has 7776<sup>6</sup>, or 2 x 10<sup>23</sup> unique combinations.

On my standard Mac keyboard, there are 94 characters[*](#keys) I can use to form leet passwords. An eleven-character leet password has 94<sup>11</sup>, or 5 x 10<sup>21</sup> unique combinations. As you can easily see, a six-word passphrase is 100 times 'bigger' than an eleven-character leet password.

People often use entropy to measure password strength. To say a password has 44 bits of entropy is to say the password is chosen from a search space with as many unique combinations as a 44-bit binary string of 0's and 1's. That is, there are 2<sup>44</sup> = 17,592,186,044,416 possibilities. Each additional bit of entropy doubles the search space. Now, we can see that an eleven-character leet has log<sub>2</sub> 5 x 10<sup>21</sup> = 72 bits of entropy. In comparison, our six-word passphrase has log<sub>2</sub> 2 x 10<sup>23</sup> = 77 bits of entropy.

One common doubt I hear is that the diceware word list is public and everyone suspects they should make their own private list. That argument is analogous to saying the letter E is on everyone's keyboard and we need a private keyboard to type. The strength of diceware comes not from secrecy but the enormity of its search space.

<a name="keys">*</a> 26 uppercase, 26 lowercase, 1-0, shift 1-0, 11 symbols, shift 11 symbols.

