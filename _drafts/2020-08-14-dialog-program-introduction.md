---
layout: post
title:  "Dialog Programming - Introduction"
author: sal
categories: [ Screen Programming ]
image: assets/images/dp1.jpeg
tags: [sap abap]
date: 2020-08-14
---
This is a beginning of new blog series in which I'll discuss Dialog Programming aka Module Pool Programming. This blog series will target the beginner who has started their journey in SAP ABAP world. In this 1st blog I'll introduce you all to the Dialog Programming, How it is different from Executable Program (SE38 Programs), and its advantages. Enough of chitchat, Let's Begin!

## <code class="highlighter-rouge">Dialog Programs</code>
Dialog Programs allows bi-directional interaction between users and the programns. Bi-directional interaction is programmed within modules. A dialog program comprises of a collection (or pool) of such modules. Hence it is also known as Module Pool Program.
A `Dialog program` is a user-action driven program of type 'M', which is created using Tcode SE80, and can neither be executed in background nor directly. Hence to executed a dialog program you'll need a Tcode which you can create in Tcode SE93.

<br><strong style="color:Green;">Note: </strong>User-Action driven programs means that user interact with the program i.e. they input data to the screen or click some buttons on screen or choose a menu item or clicking an entry.

## <code class="highlighter-rouge">Executable Program vs Dialog Program</code>
I guess from the introduction you might have figured out the difference between the executable and dialog programs. Hence I'll keep it short and to the point. Dialog program which is of type 'M' needs a Tcode to execute it and it can't be executed in background. Whereas Executable program which is of type '1', is event driven program(Load of program, Start of Selection, End of Selection etc.), can be executed in background. Also Executable programs can either be executed directly or through Tcode.

## <code class="highlighter-rouge">Components of Dialog Program</code>
1. `ABAP Program :` is used to process user inputs, contains standard ABAP/4 syntax within dialog module that are called by the screen flow logic. Here the ABAP program is Module pool program hence it will begin with keyword `'PROGRAM'` whereas in normal executable program it begins with `'REPORT'` I'm sure you might not have noticed it &#128521;.
2. `Screen :` is the user interface of the program, is identified using a 4-digit screen number. It can be designed using Tcode SE51 or in the Tcode SE80. <strong>Each screen consists of design and flow logic</strong>. Flow logic will explain the flow of the program like after this screen which screen logic will get executed.
3. `GUI Status :` provides a user with wide range of functions on sreen, is designed using Tcode SE41 or SE80. It comprises of 4 toolbars: 1. Menu Bar 2. Standard Toolbar 3. Title Bar 4. Application Toolbar
![GUIstatus](https://lh3.googleusercontent.com/pw/ACtC-3clKz1OZQzEtWCW_w6UAEBHfD87REEfKkXV0XTI5XhTPrUaqD-Or5g2ORmgC2MSd0vKstnyFS48jEP5uqBYck8zqMv5VAMbepSHHJw3CkRYaomY38OUcUi--_0ai09XSZqWV5tZpxtjvhqQGZ_yC5lb=w1440-h203-no?authuser=0)
4. `Transaction Code :` used to execute a dialog program, is linked to the 1st screen of the dialog program, can be created using either Tcode SE93 or SE80.

## <code class="highlighter-rouge"><a id="events_in_dp">Events in Dialog Program</a></code>
Basically there are 4 events which is apart of Screen Flow Logic.
1. `Process Before Output (PBO): `which is processed before screen is displayed. Present by default when a new screen is created.
2. `Process After Input (PAI): `which is processed after a screen is displayed i.e after a user action on screen. Present by default when a new screen is created.
3. `Process On Help request (POH): `which is processed when F1 is pressed.
4. `Process On Value request (POV): `which is processed when F4 is pressed.

## <code class="highlighter-rouge">Create a demo Dialog Program</code>
In this blog I'm keeping it to the inroduction part only hence I'll show how to create a module pool program in the next blogs I'll create a demo dialog program based on requirement so that you can understand.
1. Go to Tcode SE80.
2. Provide program name starting with `'SAPM'`, its a SAP standard which signifies that the program is a module pool program. Press enter. A popup will come, confirm this by clicking yes.
![SE80_DP_create](https://lh3.googleusercontent.com/pw/ACtC-3cNjruc8onsA9R5gegrqJIMpCrZtdo_7FkdVSJTxqD5gZIZKG3UhP2l2eOG6hsE4tML1gDTFky8pB3oa4LNXRUrc0x2WS0pgi6ui9comxOEHRg7k_6yHIBhOERbP0Csh2G63LD7gW9MQ2lSh0yMO7tO=w524-h366-no?authuser=0)
3. Another prompt will appear, check the checkbox 'With TOP INCL.' and if you want to change the name of dialog program you can do it here. Then press enter.
![topiclude](https://lh3.googleusercontent.com/pw/ACtC-3cGPJ1TEBUf7Wkg4Wpp8hlpPEUu4EUHb-7V1qP-YzPgrZeLLAVrHh5pNKy5EwXPZMoKpExcEFEL0CUS0Rj7eQnSHISjVLGHk8h_ECxtKF0HgnoA_ZGcrRTvoEW7u8jg2KUEJM10Q3J4lkB4AsdmgvyF=w646-h276-no?authuser=0)
4. In next prompt give the top include name.
![topincludename](https://lh3.googleusercontent.com/pw/ACtC-3edADZGe6HQjMJ811dmXjA4LC6syVwdC1ZJRjG6oUICggQW6O0wUvfDoENE27anqFBMgQY4vr7N3DHtOHaerFp6bFOqvLTibr3bPWX17B1chygxKD8QUsovFtfzlJX3prkvc0wCZ5-gO2gwia7cUrmG=w790-h222-no?authuser=0)
5. Provide Title of Program and save it.
![title](https://lh3.googleusercontent.com/pw/ACtC-3fdNUuPwm181siYFjyVuThGVgnSM_bSWpetrDUS81Xdy0r4aCDlPcKZn8_OX0AKx15s-shQVGnWvgvgJ9kiEsv27c8NF4u8paQ-9mVU18U5WWO-TyAJ8NHcqqd-R48sXjHJnSOOOGpRAhbTMSt5SF78=w1254-h714-no?authuser=0)
6. Double click on the program name 'SAPMZDIALOG_DEMO' you'll see below screen.
![DP_title](https://lh3.googleusercontent.com/pw/ACtC-3f1r9AKH9aKugvLwdCbj2R7nz9_3g9-05F6tfXWFnh0QRG6xC4XtYc40Q8tROxh7q4FP2iFNPOgTrXqA2y1ul8sak-N1BLqUZxIzKFphX-SXu74JjYDXX2ZuCdHuMPhDUm3tyD8oYXiIxYBmg1G0SDs=w1440-h524-no?authuser=0)
7. Uncomment all the include and create them and then activate all the Includes.
![activate_program](https://lh3.googleusercontent.com/pw/ACtC-3evaIDtuR2vcOlfe473h7to5JL7YMfyb-klBuSbR2J5vXw3FcAQNX2bRnAbiiM4rUNZruyvsGyLu291Qcqm72vEIornO3QBGGm5JEfSLlBy8M_YdJ5YlagRmbNkaqky5YJjciNmV26m0-Mo_CvDe6XQ=w1440-h680-no?authuser=0)

So now you know how to created a Dialog program. In the next blog I'll explain working with Screen and GUI status and create a Tcode to execute dialog program. <a href="/dialog-program-with-screen-gui">Click here to check next blog.</a>
