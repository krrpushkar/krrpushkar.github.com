---
layout: post
title:  "Implicit Enhancement"
author: sal
categories: [ Enhancement Framework, tutorial ]
image: assets/images/implicit.jpeg
tags: [featured]
---
Let me explain the `Implicit Enhancement` in ABAP report in this blog and then similarly you explore other Implicit enhancements in other SAP objects. So there are two places where the enhancemnts are possible by default. One is at start of the report and other at the end of the report. So by default you can do enhancements at the start and end by creating enhancement implementations.

## <code class="highlighter-rouge">Find Implicit Enhancements.</code>

1. Go to `SE38` and open any standard report.
2. From menubar select Edit->Enhancement operations->show implicit enhancement options.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3esg0cUzpgnkjzSjPSE95afSGRjYc6uH6vF2hycOiLiPdA_KPsEZrzucm7q-skpan_hgZKJJY_Gr7DQrvE0Eg8OcuiV6WmBj8c0yn8ZNoc7wWIwOVmYAjDXANgwlpenkNoRfeZKMLpqZwjciWUSCqlp=w942-h564-no?authuser=0">
3. You'll see some extra lines in your report like below. And if you are in change mode then these lines will be visible in yellow color.

```
"""""""""""""""""""""$"$SE:(1)

```

## <code class="highlighter-rouge">Implement Implicit Enhancements.</code>

1. Go to Program->Enhance.
<br><img src="https://lh3.googleusercontent.com/pw/ACtC-3cAc-KGXVf3klMsWHuTQzrnp7_jke8y-1FjS9jgUUVOJm-gNgCu0QS0SqOfZN0t38S0rDRVJ-F-lvZcwT1Ivb116WJWO1hpNxKgUcHp46EpDfcUS-zQgum2RAp1qWjwxpex6j0YGgJS3k3CoByeJERs=w376-h484-no?authuser=0">
2. Go to Edit->Enhancement operations->create Implementation.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3cWy_CGa0V3IbvChf89bA3gucZh05mTG_Vjb6PygB53x78k-M6tAkV7qivBjBZXWKvpGO27kJhxMOhQEXa49xDEdy_xh4_MF4qv4-INEfTMV7KNGcp063VgcmASq9LrxJO3SSDPwcWYGpdobiTcV2zz=w1082-h522-no?authuser=0)
3. Give Implementation name and description and continue.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3f1SMJ89iDBsZpghStBDtY8PCNQTTl2CAnanKXIZ8uqseug8MWT9MUVyI7AbXaELL2bHCfBoo0K0FeU-aGJKwdx0Fg2GCG4LE10Njol5fo-5jV7CJ4Phx59QlfwG0B-CeaaurV_PFz7DQC4pN20LJzt=w1440-h253-no?authuser=0)
4. If popup comes then choose 'CODE'.
5. Finally write your logic here according to the requirement.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3esAv5aNEWOoEqpEqwxhYc3_0l20EGqtAoXWAmWsrAG7Wuk-7EEH7WzclNR1suog5qb1GZZHebo6WlirUu890gL1ehqpVgKztHrfMVd2OqQAumCpoMUV_q0CWW3W_SMbFeVFzjQtWB3jVQosDJJDU3A=w1428-h190-no?authuser=0)

<!-- ![walking]({{ site.baseurl }}/assets/images/3.jpg) 
Here's a standard YouTube embed code as an example:

<p><iframe style="width:100%;" height="315" src="https://www.youtube.com/embed/Cniqsc9QfDo?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe></p>

-->