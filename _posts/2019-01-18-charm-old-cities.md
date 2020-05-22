---
layout: post
title:  "Enhancements in ABAP"
author: sal
categories: [ Jekyll, tutorial ]
image: assets/images/enhancement.jpg
tags: [sticky]
---

Enhancement represent potential customer requirement that have not been implemented in the standard software. The standard software enables the further developement of such exits at the customer site, using logic specific to the customer.
Before going into the Enhancement lets understand the difference between the <b>Enhancement and Modifications.</b>

#### Difference Between Enhancement and Modification

1. <b>Modifications</b> are changes made directly into the SAP delivered objects( also called core modifications) Whereas <b>Enhancements</b> are additions or insertion at predefined points in SAP Objects. 
2. Apart from the definition the main difference is <b>Modifications</b> are overwritten during SAP Upgrade or application of support packs and have to be reapplied/adjusted after the upgrade but that is not the case with <b>Enhancements. </b>
3. <b>Modifications</b> are not provided by SAP whereas <b>Enhancements</b> are provided by SAP.
4. In <b>Modification</b> you'll need object access key whereas in <b>Enhancement</b> you won't.

I hope now you have got the idea that the Enhancement concepts allows you to add your own functionality to SAP’s  standard business without having to modify the original applications.

Now lets see what are the different ways to enhance SAP objects.
<!-- Types of enhancement -->
<ul id="enhancements">
<!-- user exit -->
  <li><span class="caret" style="color:blue">User Exit</span>
    <ul class="nested">
      <li><span class="caret" style="color:teal">What it is?</span>
        <ul class="nested">
          <li><p>User Exits are nothing but adding additional functionality to the standard functionality using the subroutines( FORM ENDFORM). Hence it is also called Form Exits. In real time scenario user exits are used in the SD module.</p>
          <p>Lets understand this with an example: In real time scenario, we need to maintain the key information of the sales order in a separate ‘Z’ table while creating the sales order.  Now if we need to delete the sales order then we have to delete the corresponding information from the ‘Z’ table too. And this can be done using User Exit : USEREXIT_DELETE_DOCUMENT.</p><p>Now you all must be thinking how an ABAPer would know all the user exits and their functionality beforehand. Let me tell you that it is not an ABAPer’s job to know which User exit to use, it is Functional people’s job but there’s no harm in knowing where you can find the user exist.</p></li>
        </ul>
      </li>
     <li><span class="caret" style="color:teal">How to find it?</span>
        <ul class="nested">
          <li><p> There are various ways to find it but let me tell you the simplest way, Go to object navigator( SE80 ) ->Select package and put VMOD and press enter-> You’ll get all the list of the user exits and go though the description one by one to find the right one for your requirement. You all must be like WHAT! how are we going to find the right User Exit but in my defence I already told you that the Functional people will tell you the name of the User Exit for your requirement &#128513;  One more approach to find the User Exit for the given transaction is go to transaction (e.g VA01) -> Status -> System -> double click on Program(screen) name -> chose your related Include -> chose your related User Exit.</p>
          </li>
        </ul>
     </li>
     <li><span class="caret" style="color:teal">How to implement it?</span>
        <ul class="nested">
          <li><p>Go to SE38 and enter program name ‘MV45AFZZ’ and click on display. Click on find function key and provide your User Exit name and press enter. Double click on user exit or form and identify the place where our logic should be written( this is ABAPer’s job &#128513; ). Click on enhance icon on the application tool bar. In the menu bar click on Edit -> enhancement operations -> show implicit enhancement options -> It will provide the yellow line for all the forms -> select our user exit yellow line and right click -> enhancement implementation -> create -> click on code -> Either you can choose from existing Enhancement implementation or create new enhancement implementation -> provide implementation name, description and save( either in local or your package ) -> select the implementation name  and provide the logic.
          </p></li>
        </ul>
     </li>
    </ul> 
  </li>
<!-- Customer exit -->
  <li><span class="caret" style="color:blue">Customer Exit</span>
    <ul class="nested">
      <li><span class="caret" style="color:teal">What it is?</span>
        <ul class="nested">
          <li>Black Tea</li>
        </ul>
      </li>
     <li><span class="caret" style="color:teal">How to find it?</span>
        <ul class="nested">
          <li>White Tea</li>
        </ul>
     </li>
     <li><span class="caret" style="color:teal">How to implement it?</span>
        <ul class="nested">
          <li>Black Tea</li>
          <li>White Tea</li>
        </ul>
     </li>
    </ul> 
  </li>
<!-- BADI -->
  <li><span class="caret" style="color:blue">BADI</span>
    <ul class="nested">
      <li><span class="caret" style="color:teal">What it is?</span>
        <ul class="nested">
          <li>Black Tea</li>
        </ul>
      </li>
     <li><span class="caret" style="color:teal">How to find it?</span>
        <ul class="nested">
          <li>White Tea</li>
        </ul>
     </li>
     <li><span class="caret" style="color:teal">How to implement it?</span>
        <ul class="nested">
          <li>Black Tea</li>
          <li>White Tea</li>
        </ul>
     </li>
    </ul> 
  </li>
<!-- Enhancement framework -->
  <li><span class="caret" style="color:blue">Enhancement Framework</span>
    <ul class="nested">
      <li><span class="caret" style="color:teal">What it is?</span>
        <ul class="nested">
          <li>Black Tea</li>
        </ul>
      </li>
     <li><span class="caret" style="color:teal">How to find it?</span>
        <ul class="nested">
          <li>White Tea</li>
        </ul>
     </li>
     <li><span class="caret" style="color:teal">How to implement it?</span>
        <ul class="nested">
          <li>Black Tea</li>
          <li>White Tea</li>
        </ul>
     </li>
    </ul> 
  </li>
</ul>