---
layout: post
title:  "BADI Definition"
author: sal
categories: [ Jekyll ]
image: https://images.unsplash.com/photo-1460925895917-afdab827c52f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=1002&q=80
tags: featured
date: 2020-05-21
---
Before starting this let me tell you one thing you'll rarely create BADI Definition in real time scenario. Generally you'll use existing BADIs,<a href="#here">How to find it?</a> <br><b>SE18</b> is the T-code for BADI Definition. But before creating BADI you'll need a container for it i.e an Enhancement spot. This is the container in which you'll develope your BADI.

## How to create an Enhancement spot?
1. Go to object navigator( SE80 ), navigate to the package in which you want to create the enhancement spot.
<a href="/function-module-exit#exactline">How to find package name? click here.</a>
2. In the context menu of the package choose <br>Create->Enhancement->Enhancement spot.
3. Enter the name and description and save.

## How to create a BADI Definition?
1. Within the same Enhancement spot, choose the create badi pushbutton on the left.
2. Give name starting with 'Z' and short description of the BADI.
3. Choose the type of the BADI.

<p>So the BADI creation is done? NO, you still need an interface where you'll define your method and while implementating the BADI actually you'll implement this method and write your logic.</p>

4. Expand your BADI name and you will see the 'interface' icon.
5. Double click on it and provide an interface name( either existing or a new one ).
6. Click on change pushbutton this will take you to the class builder where you can create the method you need for your BADI. Simply now provide the method name and parameters for the method.
7. Save and activate your BADI as well as Enhancement spot.

## <a id="here">How to find Existing BADI?</a>
1. Execute SE24. Provide the object type as ‘CL_EXITHANDLER’. Click on display. 
2. Double click on GET_INSTANCE method. 
3. Place the break-point on first call method. 
4. Now we execute our required transaction (which transaction BADIs we want) in a separate session.
5. In the menubar click on debugger -> switch to classic debugger. Provide the field name as EXIT_NAME. Press Enter and Identify the BADI. Continuously click on F8 button. Identify the all the BADIs & maintain in Excel sheet. 

After that delete the break point. Now open the each & every BADI in ‘SE18’. Click on display. Click on interface tab. Double click on each & every method. Identify the input, output parameters. In the menu bar click on goto -> documentation -> to component. Read the documentation if it satisfies our requirement then we implement this method through SE19.

Confused? - Hence in the real time we always identify the BADIs with the help of functional people &#128512;.