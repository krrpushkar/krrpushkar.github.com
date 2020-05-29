---
layout: post
title:  "Standard BADI Implementation"
author: sal
categories: [ Enhancement, BADI ]
image: assets/images/badi-implementation.jpeg
date: 2020-05-22
---

Before Implementing any standard BADI, let's see <a id="here">`how to find one first?`</a>

1. Execute SE24. Provide the object type as `CL_EXITHANDLER`. Click on display. 
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eY9hugumL6pQfalnY5uVKTPAke5_br0ym7o5TYuxbHfdA5NFVL66JC63mjybF2Un5cLVYV-WoWijc0Jsql6efs2ROs0BWZHnPOd5xxvrUBOe-L3Zh8OGRpcWgLWKcXkyWdHXC789m7VzuXl692YsQH=w832-h374-no?authuser=0">
2. Double click on `GET_INSTANCE` method and place the break-point on first call method i.e `cl_exithandler=>get_class_name_by_interface`.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3dnhZUQtGXZ0xu8kSftXhtS23vyXSASn3KvNYhrMS3hwHBDzanSfhPSqcp6SGnjGUPtsZU31TNESmKuFzSGkXsBCFJ9vyVHsJZyD8oQ9Y_x-iGPyEDOSGEfyEihx78d-mo6KPzSpkywJ3A6m-_VjBDg=w909-h788-no?authuser=0">
3. Now we execute our required transaction (which transaction BADIs we want) in a separate session. `USE CASE :` Let's display a message when a specific type of material is created in `MM01` T-code.
4. In the debugger provide the field name as EXIT_NAME. Press Enter and Identify the BADI. Continuously click on F8 button. Identify the all the BADIs & maintain in Excel sheet. <br><br>After that delete the break point. Now open the each & every BADI in ‘SE18’. Click on display. Click on interface tab. Double click on each & every method. Identify the input, output parameters. In the menu bar click on goto -> documentation -> to component. Read the documentation if it satisfies our requirement then we implement this method through SE19.<br><br>Confused? - Hence in the real time we always identify the BADIs with the help of functional people &#128512;.
<br><br>Here `BADI_MATERIAL_CHECK` can be used.
<br><br>5. Go to `SE18` and open `BADI_MATERIAL_CHECK ` and from menu option Implementation -> Create
<img src="https://lh3.googleusercontent.com/pw/ACtC-3diWeZd_jo_6sTBYBQO3J8j3sP8xlc0EUnInjVC1W4m7Csr4ApSHU4DieZdCRhOta0oTa7ytBYqI1NjMk4p3s79u8DYkJvtRdjkj_XIlgJZ50Iaahf8PLTyhi7Nqf1lhRVP0xh8GBFwBUT997ZaOdpJ=w1348-h422-no?authuser=0">
<br>6. Give Implementation name and save.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eSiGLmpTJ2wSeU1BXu7GVJdiwVEDWMr751Ig-c110TwNoglehOk2ow_brbRrYY0DjGir4Afd5NYGiV8NfNNYO61_sssBzzQAn7wSUwh853N0rWKSDDJmgTYOdCC9GVY-2aSCB6P6T3QnyP1aAj09RH=w1178-h432-no?authuser=0">
<br>7. From the interface tab click on method `CHECK_DATA` and provide below logic.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3c-gnWUn_jEKYn7m7q6Gns_ObjP_dU8-AINdj01n-dnifpqyLvSLogfSIrs1vGkXBuTmSc23fkQmRpxNi9zt0d8mSdcmGDm77h5mjAHqG37qd2fpH2oz6nzjVg5NubYakYDPiQ40PfJPElqtXeUs09H=w867-h788-no?authuser=0">
{% highlight ruby %}
IF wmara-matkl = '20'
AND wmara-spart = '02'.
 MESSAGE 'Demo BADI Impementation' TYPE 'I'.
ENDIF.
{% endhighlight %}
<br>8. Go to `MM01` T-code and create material. If you are wondering what to fill in the input fields, go ahead and fill anything in Material, Industry Sector and Material Type. You can take help from below screenshot and Press Enter.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3c2ggCHKkH3OVOWtbGNaoiGdzfWaUnGsUATNX2wSDQcqy51A3_Zkez2xF6KA54Ml9nekHHl1vqafs0Oplk62MTELlmk3uAY9egz-kFkA2576b1f4fphBGXhPTgC-OXCQSYM5SpII3N-40Z6JARjF4ym=w570-h510-no?authuser=0">
<br>9. Now choose `BASIC DATA` for the select view(s).
<img src="https://lh3.googleusercontent.com/pw/ACtC-3fFM2U2UY-qnlfjN930HqZfo3ead8tdBssvgPattDrKARyD-N4oeJNL-o52enUdCQvPHPCXD2VLZKb6EcZNOQkgMK-YR2m3MpIl1S190mOx0XLRzJLnWqj_tSqFVmd1LjtFRpnmWDa_Qt9n0UFkTl2a=w615-h788-no?authuser=0">
<br>10. Provide Material Group as '20' and Division '02' and save.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eI5ezQXujAPdiJznFW9epSD6hmPj9TWT1-QYWZvlLJGVfbC1nh48C3EKv4IOPo-hFRGNx2a4U5SSVeDhXR9n6p4Qm7fJqdJxPNeJ3y7scKMelYp3Qo1mwi5z2rSJZ8C4qcwNClqdY0FB9IPRS07IX5=w1166-h318-no?authuser=0">
<br>11. After clicking on save you will get the message 
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eCgdptkqVt_TAYICpO9XC8iee8e6ABTDCyhbyHDvJpsnK9TMI8metQm_qaLMZfdiMTFhMADHT3GMDtoxKo_txM_nzHlbPAdlCxLyhJDnJ4s2eXjo-n17kLLLpf5ztj22dHKqlfilpr93MPRNwcwcKY=w876-h270-no?authuser=0">

`Congratulation!` you implemented your first standard BADI. 
