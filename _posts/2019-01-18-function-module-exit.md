---
layout: post
title:  "Function Module Exit"
author: sal
categories: [ Jekyll, tutorial ]
image: assets/images/function.jpeg
date: 2020-05-21
---

<b>Function Module Exit</b> is nothing but function module with 'Z' Include in it. And inside this 'Z' include you have to put your custom code.

<b>Confused?</b>

Okay, let's understand this with an example. Suppose there is a requirement to display custom welcome message when an user log into SAP system. By looking at the requirement we can say for sure that it is related to User maintenance i.e. SU01 T-code.
Now what we have to do is, simply find the package for the T-code, after finding the package we can find the Customer Exits. And then choose the Customer Exit for our requirement and implement it. Again let me remind you in real time scenario Functional people will let you know the correct Customer Exit for the given customer requirement, so don't worry about this But as I said earlier there's no harm in knowing &#128512;.

## <a id="exactline">How to find the Package of any T-code?</a>

Simplest way is to : 
1. Go to SE93 T-code.
2. Give your T-code (SU01).
3. Click display and voila! you'll know the package.

## <a id="exactline1">How to identify the Enhancements or Exit name based on package?</a>

1. Execute SMOD T-code.
2. Click on find button on Toolbar or go to Utilities->find in Menubar.
3. Give the package name and execute. You'll see a list of Enhancements or Exit name.

 So now after going through the description we can identify the correct Customer Exit. I know its a little bit boring to go through all the Exits as an ABAPer but I hope you know the next line &#128514;. But here for our case there will only one Exit <b>SUSR0001</b>, and from the description you can see that this Exit is called after user log into system. So now we just have to implement it.

## How to implement an Function Exit?

1. Go to CMOD T-code and create a new project starting with 'Z'.
2. Click on Enhancement Assignment and provide our Exit name (SUSR0001) and press enter.
3. Go to component window and double click on required Function Exit, here in our case there will only one i.e. EXIT_SAPLSUSF_001.
4. Double click on Include ZXUSRU01 and write your logic there.

{% highlight ruby %}
IF sy-uname = <userid>.
    MESSAGE 'Welcome to SAP' TYPE 'I'.
ENDIF.
{% endhighlight %}

<br><a href="/menu-exit">Next Menu Exit</a>