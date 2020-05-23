---
layout: post
title:  "Screen Exit"
author: sal
categories: [ Jekyll, tutorial ]
image: https://images.unsplash.com/photo-1584091377251-b435d5e47c0f?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60
date: 2020-05-21
---
Screen Exit allows you to add your own fields to specific screens in standard transactions. This can be achieved via customer specific subscreen. The process is same as Function as well as Menu Exit i.e first we have to find the package name and then according to package identify the right enhancement( or Exit name ) for our requirement. If you have gone through my previous blogs you'll understand easily so I recommend you to go through them.
<br><a href="/enhancements">Enhancement Overview</a>
<br><a href="/function-module-exit">Function Module Exit</a>
<br><a href="/menu-exit">Menu Exit</a>

Okay as I have given an example in each previous Exits similarly we'll understand this one with one example. Lets assume you have to add some customer specific field on the header section of the screen in ME21N T-code( to create purchase order).<a href="/function-module-exit#exactline">Find package name</a> i.e 'ME' and similarly <a href="/function-module-exit#exactline1">Find enhancement or Exit name</a>, for our case it is 'MM06E005'.

## How to implement an Screen Exit?
1. Go to CMOD T-code and create a new project starting with 'Z'.
2. Click on Enhancement assignmet and prove Exit name( MM06E005 ) and then click on components.
3. You'll see two include tables at the bottom choose according to your requirement here I'm adding new field in CI_EKKODB( in EKKO table if you want you can add in EKPO table instead). Activate it. One Include is created in EKKO table.
4. Come back and click on program 'SAPLXM06'. Select subscreen option( in screen type ) and click on layout.
5. Design your screen and come back to flow logic. Only designing a subscreen is not enough you have to write the logic to send and receive data from this subscreen.
6. Define module in PAI and PBO. Activate it.
7. Coming back to your project, your back end table extension and screen field is ready. Now you just have to write few lines of code to read the screen input field and put it back in the back end field in PO create( ME21N T-code), so that if neeed you can retrieve it using T-code ME22N or ME23N.
8. For the previous step you have to use Function Exit 'EXIT_SAPMM06E_008' to read the screen field and putting in the back end table field. Double click on 'EXIT_SAPMM06E_008' and find the Include 'ZXM06U37'. But before editing the Include you have to change the structure 'EKKO_CI' to read the screen field. SO go to Changing tab and double click on EKKO_CI and add your screen field.
9. Now edit the Include program and map this screen input field to the changing parameter.
10. You'll have to use another Function Exit 'EXIT_SAPMM06E_006' to retrieve the value of new field and show on the screen. Similar to point 8 you'll have to change the Importing parameter 'I_CI_EKKO' and inside the Include 'ZXM06U36' map it to the screen field.
11. Activate the project and execute ME21N. You'll see one new tab 'Customer Data' where you can find your new custom field.
12. Go ahead and test it, create new PO( Purchase Order ) and in EKKO table you can find the entries. Execute ME22N and provide the same PO number and you can see new screen field.
