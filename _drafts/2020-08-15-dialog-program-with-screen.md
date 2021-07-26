---
layout: post
title:  "Dialog Programming - Working with Screen"
author: sal
categories: [ Screen Programming ]
image: assets/images/dp2.jpeg
tags: [sap abap]
date: 2020-08-15
---
In the <a href="/dialog-program-introduction">1st blog : Dialog Program - Introduction</a> of the series 'Dialog Programming', I gave a basic introduction of the Dialog Program. In this blog I'll be working with <a href="#screen">Screen</a>, also I'll <a href="#tcode">create Tcode</a> for my demo program.

Let's start with a quick intro to the screen, as you know it is a graphical user interface that enables users to interact with the backend application. It is indentified with a 4 digit unique screen number, except 1000 which is a SAP standard selection screen. It consists of **Attributes** (properties of screen), **Layout** (design or arrangement of screen elements on screen) and **Flow logic** (contains the program logic). There are 3 types of screen :
1. **Normal :** A normal screen occupies the entire GUI window.
2. **Subscreen :** A subscreen is displayed as part of another screen.
3. **Model Dialog box :** A model dialog box is like a pop-up window, which covers only a portion of the GUI window.

## <code class="highlighter-rouge"><a id="screen">Working with screen</a></code>
Let's create a screen in your program then.
1. Go to your program in SE80 and right click on the program name, select create, then select screen.
![screen](https://lh3.googleusercontent.com/pw/ACtC-3cHf1doQ6SUb0yzco_JLGm_aVKsfPb210eLSru-SrMzHIlX91jxjUibR3_Xtyv5l9DISmsByT8wtmNgmy9jCeYEtcyZD5l-G4JQt8bJhBCa6-dJF67W_gQ31LafeN7wHGJFmkfrEoXJWdBRHMeKHvO-=w988-h714-no?authuser=0)
2. Provide a screen numer in the popup and press enter.
![screen_number](https://lh3.googleusercontent.com/pw/ACtC-3fh1yU7xnp0Zr5u424fQFmU-_fmut598XhZCF7PB-6TKdl_qicVhgYYyWD2lbaJuS9m4pABEur140ZN3dIxu1nHH-BTT87LET4WLsgNIwCJ8c494MIOMrAoCUEfHu-EobIaZdp-9IALNiD5baoQqQVO=w702-h228-no?authuser=0)
3. Provide description of the screen. And save it.
<br><strong style="color:Green;">Note: </strong>Do take a look at the next screenshot.
![screen_description](https://lh3.googleusercontent.com/pw/ACtC-3depad-X_cQRE2gYHBPAydyd4sS8SkoqfXoVjHO-PcOc1dZotD2TaqwqMSqQnSsqeuHcmd-vMErH1raBKjj70F3A5aslo0g9EhARwjPlRiY8On-1cfxDiEYFuZ5NiY7ceKWIhi3cFxCzQY9V_nDxVR2=w1112-h714-no?authuser=0)
4. Click on the layout button and design the screen according to your requirement. Here I'll create a simple screen to add two numbers &#128512; Okay so go to 'Edit' mode and then click on '<b>Text Field</b>' icon and then click on the screen and place them on desired place, similarly after clicking on '<b>Input/Output field</b>' and '<b>Pushbutton</b>' clcik on the screen and place them on the desired place.
![screen](https://lh3.googleusercontent.com/pw/ACtC-3eMIDZu_ZL-e_RsmYphyU7PRyk2fH4mtXx9d9bOSwzy86Br41j7MV-ComdOPL1GR8i_ZMslXKXryO4yhR1M428iiMcngSfIP2LIX6Ki-kZ3VbMwOePefgV-3HXaVlfiTHv2vzgDXKXvJL7Ry87clexN=w618-h387-no?authuser=0)
5. For <b>Text Field -</b> `Text` is mandatory field, for <b>Input/Output field -</b> `Name` is mandatory and for <b>Pushbutton -</b> `Name` and `Fctcode` is mandatory fields. 
![textfield](https://lh3.googleusercontent.com/pw/ACtC-3dIHVE2BA8VvF3KtkfcjW3vE95hSn0AxvVPdTHOyp5aj8uigZP5IjNzid_l8gIZxIjRI5FP52JJJJ5zwTE38CMMZQQp9d5wCBuoSAaKUAFteNUhSy07oSPABQQ0cDuzBg1FoOfOOeZhfXbZ4Zqq7xsQ=w232-h398-no?authuser=0)
![i/ofield](https://lh3.googleusercontent.com/pw/ACtC-3eQEafyx-E0l6ay6-4qCa0TCYy9qFTBbht8OLpPsfcQkiH40CEqOhKwpc8mozfDURX94t3fTgDXKXRSbI-o_djnlUxfMu9JFxq1vvNIxN8pLM-soddc6iQFlgIFie7lOtvbIKnIro5x0VWsW6nLqxc7=w231-h371-no?authuser=0)
![button](https://lh3.googleusercontent.com/pw/ACtC-3evpJGJhCrh7SxNzxbszouev1d_ycHXVRRd-uSw9vSwzeRnt6P7h_mKS8Q4_h6Q0ZhE-rQqOqARlBRFb4DXGG5IGzsbPQZhjMqL7s6TigI4ipFSscWp26IwogpC1nIOVQrr7FKNBq2X1N9ephxu_dSu=w230-h371-no?authuser=0)
6. Now if you notice the result field is disabled, for this you choose Input/Output field and in the attribute tab of the element select checkbox `Output Only`.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cIc6ijiNoiMdsejZsP1Yzzt1xO_-XbqFFOz6pbvKz81G3ONv9HhSsVkIyt-TI0xiV2WDxBoqCLLArmYebhchIlRsjAYOtLajKuuQj9faHn_akwiuP1_uJVVa4YWtAs5HduLLoa0IQob2ISGXPAI8rQ=w223-h520-no?authuser=0">
<!-- ![output](https://lh3.googleusercontent.com/pw/ACtC-3cIc6ijiNoiMdsejZsP1Yzzt1xO_-XbqFFOz6pbvKz81G3ONv9HhSsVkIyt-TI0xiV2WDxBoqCLLArmYebhchIlRsjAYOtLajKuuQj9faHn_akwiuP1_uJVVa4YWtAs5HduLLoa0IQob2ISGXPAI8rQ=w223-h520-no?authuser=0)  -->
7. Now you are done with screen designing, Let's write some lines of code to execute this.

## <code class="highlighter-rouge"><a id="tcode">Data Flow/Data Mapping</a></code>
After designing the screen, the question will come in your mind how will you access the input value provided on the screen? In other words, how will you map the data from screen to ABAP program? To map the data from screen to ABAP program, you need to keep in mind below points:
1. Contents of screen fields are passed to identically-named fields in the ABAP program in the PAI event, and filled from the same identically-named fields in the program in the PBO event.
2. An Input/Output field created on screen should be declared with the same characteristics with respect to the data type, length etc. In my program it is 'INPUT1', 'INPUT2', and 'OUTPUT1'. 
![Top_Include](https://lh3.googleusercontent.com/pw/ACtC-3d1u6o1QVWYQByGXnC3ZSAOnjXUUZRB9yqupTtCV6vN4l9KoAbQGJ5t-ibfdhZi3zSgtQu_g77ZLLIXzMxkoYdM3Rt7484NsgSot-Pveo8elSeI-YnwB8UGrm1fKHuyjHHkNioLLyaKk7KxgRFNekqb=w557-h227-no?authuser=0)
3. Text fields, pushbuttons and boxes do not need any data declaration. In my program Text fieds 'T1', 'T2', 'T3' and PushButton 'Button1' need not be declared in TOP Include of the program. As you can see in above screenshot of TOP Include.
4. When you click on any PushButton on the screen, it captures their Function code of the Pushbutton and send it to the program. And in the program through a variable of type **SY-UCOMM** you can capture it. `When you create a screen automatically a field of type OK is created in the element list of screen.` 
![ok_code](https://lh3.googleusercontent.com/pw/ACtC-3cq_LdmpTMVtUOO5KY1jgCYCYncBWre8P_61_KtBf2XWIwwZpedrMqPoEsQYvTBQaEie7ctnILYji0CwXLSoiJ5gXFw-kwWqFFg8govlKcWDja9AySG8U7EmWb0fU-CMtyC_SvFeVQAItVUGgpwgacc=w866-h235-no?authuser=0)
5. Provide the name of the field as you like but generally 'OK_CODE' is used. And in the TOP Include define a variable with same name of type **SY-UCOMM**. Please check point 2.
6. Elements like tab-strips and table controls also need to be declared appropriately in the ABAP program. I'll explain this in detail in further blogs.
7. A checkbox or a radio button on screen should be declared of type C length 1 (value 'X' denotes selection). This also I'll explain in further blogs.

## <code class="highlighter-rouge"><a id="gui">Screen Programming</a></code>
In sreen programming only limited keywords can be used to write code, which are <code class="highlighter-rouge">MODULE, FIELD, ON, VALUES, CHAIN, ENDCHAIN, LOOP, ENDLOOP and CALL</code> rest other ABAP statements are not supported in screen flow logic. Lets write our logic then, one more thing you will write your logic in the Module of PAI( Process After Input ) event as you will process the user inputs from the screen. if you don't remember the Events in Dialog Program <a href="/dialog-program-introduction#events_in_dp">Check here.</a> 
1. Go to Flow logic of the screen and double click on Module name under the event PAI to create a new Module Program. Press Enter and save it in the Include ending with **F01.**
![PAI](https://lh3.googleusercontent.com/pw/ACtC-3eg8ffoY6FlUhGthyzdLYP-6lUbofIQU22PObhYX-Ymg4Lnwru-8ToLZE6Y1BC2X3waxcFgRaoJX2WdXafih5bToY6mZgO-8AiFUkrpex7qerALs_83l1JBvSaLCcB3ruNaf5O1NUHJyxXJ_8W7Bn7_=w480-h151-no?authuser=0)
![PAI_save](https://lh3.googleusercontent.com/pw/ACtC-3dPhutgs3by_ONIUz-ewv48wYiGSGX_3_bTEpCO2GMOrflQW7Tfl1ftLeQ--ipZuVPraJ6nCWuV6S7z3cwENgTL9QGPe98frzYtrvg1BK9XpKgOhXYy5tnd1nJ6dH1HsycYZ7Sm0yXfNJyh3L6rV77o=w594-h293-no?authuser=0)
2. Again double click on the module name **USER_COMMAND_####** #### is the screen number and write your logic there.
![logic](https://lh3.googleusercontent.com/pw/ACtC-3ee4INoN_ivYSX7wPsVEoL4v9uu0KHzAuV72cNrghN8BcsJdrUbuaO4yzJz__zLCozz4N07BmSf56pZYsSllIbMY2S3S5e8pJI6l_hKEmsiWgavPFR7DNfNPUNDBGZxJ3QCHF8SKGOCO9o7_IRF4fDq=w792-h387-no?authuser=0)

## <code class="highlighter-rouge"><a id="tcode">Create Transaction code</a></code>
Now try and execute your module pool program using F8, You'll get a message 'Select an executable object', thats because module pool programs cannot be executed directly. So you have to create a Transaction code for that.
1. Right click on program name select create->Transaction.
![tcode](https://lh3.googleusercontent.com/pw/ACtC-3dyBfkyPfB163Ico8VKNVFaPGkQOjB0Q3ScY3FMn7uDft4RVuYke5DTJSLUTHKIUqorB67bzvUwuve0_bJdk2wezhWhwpihWNfqflxddkVfPFswcmOM2wOlTfFEoeU4S_awJnkgQBJz0woC81ydEcwy=w576-h319-no?authuser=0)
2. Provide Tcode name and short text.
![tcode_desc](https://lh3.googleusercontent.com/pw/ACtC-3dKP_MAFbgQeGHQ1WMDkeNQThikP8UK9GqD31BxhhKbKqmsgMYGwL8FkUFhOQ_ea5wJiFV3F7Yd5ULfZKDGTzuAgOQlehRT_XN0CtahVyaLJEjMFD6JWSCa44XVnP6XyFpAYur5Zhko5p0g60Nh_LOi=w517-h345-no?authuser=0)
3. In the next pop up provide the screen number( When you execute this Tcode, this screen will come first) and program name and select the checkboxes for relevent GUI support.
![tcode_desc](https://lh3.googleusercontent.com/pw/ACtC-3dLpoQDynVlemMItn_PzbFFdei2xVdmHPIjeeGEOFOGJf4W9zX0cBU8xBP1XFAq_UrbyimMqccLmqgHHsb38AWiz9tIjed-D_8KU6fidUzc-uRRF6r1reIx97bndm33zIqV63tAwc4CFZazyf1lgWMN=w463-h484-no?authuser=0)

Now execute your transaction( Right click on it and select direct processing or Press F8). You'll get below screen.
![output](https://lh3.googleusercontent.com/pw/ACtC-3fZpFqOGTMj0FpcV9B5I9UXA8I7urdtUMZgyW-8Kf4dSAT7vp6kUZz7cB1petv7UG4noBu83U0lXRQn7RPNoK9l6td3kxTdWmGsz7rAx6ncppS62WOpBTe5Dn5Qgx0lmoep-D-vbvoVTkJZzIHauOID=w598-h359-no?authuser=0)
If you notice, the **Standard Tool bar** is inactive and **Title bar and Application tool bar** is blank.

So how can you activate Standard Toolbar and display TitleB ar as well as Application Toolbar Or display certain button as per the requiremets? You can do all of this in the PBO event. I'll explian it in <a href="dialog-proram-with-gui">next blog.</a>
