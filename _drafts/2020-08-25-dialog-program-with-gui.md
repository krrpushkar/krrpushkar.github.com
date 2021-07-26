---
layout: post
title:  "Dialog Programming - Working with GUI"
author: sal
categories: [ Screen Programming ]
image: assets/images/dp3.jpeg
tags: [sap abap]
date: 2020-08-25
---
In the previous blog of the series 'Dialog Programming' I have given brief <a href="/dialog-program-introduction">introduction about Dialog Programming</a> and <a href="/dialog-program-with-screen">introduction about screen Programming.</a> If you haven't gone through my previous blogs I'd recommend you to go through it.
In this blog I will explain about the GUI status, and how can you activate the few or all functionalities of the standard Tool bar and Application Tool bar.

### Some points regarding the GUI status are as below:
1. The **Standard Toolbar** is common to all the screens, it contains a fixed set of 16 functionalities, to enable a functionality just provide the function code to it.
Standard ToolBar looks like below.
![Standard toolbar](https://lh3.googleusercontent.com/pw/ACtC-3dxk7onDjZsW5PHXd13H8x-9B4T86KzAvnf-pIGBEf70PgTqT6YF34N1ZAaTOlTbKupo5WuFKZY3KCGRwHdJ7mpG5JJv5kVIbNZJZ6vILhoM17JCj5DfV6INcx5xbfwtmCH2qirWY6qGgXPZNflDJ4B=w568-h38-no?authuser=0)
2. The **Application Toolbar** contains maxmimum of 35 functionalities.
3. In the PBO event, create a module program ( automatically created after the screen is created ) and inside that write the logic.
4. GUI options can be dynamically disabled or hidden using 'EXCLUDING' addition of SET PF-STATUS.
`SET PF-STATUS 'xxx' EXCLUDING '<FCT_CODE>'.`

### Let's set the GUI status:
1. Go to PBO of the screen and uncomment the statement 'MODULE STATUS_0100' and create this module inside Include ending with **O01**.
![create module](https://lh3.googleusercontent.com/pw/ACtC-3dgg8wX6pLovn0M95c0yABjxT_0WxyCjSIodPASdUs8tTv9CyAkwKnifJc22pWpM-zgARxmjeQg-E52b20c1rNw49pdDyJ43zLPNYNi7HhLQW3nto7-6Tqde79hl9a7l_x_S23gelFoJBC5j8YNLRLv=w591-h288-no?authuser=0)
2. Once you create the Module go to that Module by double clicking on it and you'll find below code is already written.
![PF STATUS](https://lh3.googleusercontent.com/pw/ACtC-3ffxnIrUeGCHsI7iMcTueKzyLaWq8ri13uRUjjfxR-h8hNPQ9qdEdkxOXLwu7MZQbsqMnQCQRH3mOleG4_y-9MarmPriJ1sdb6D8m6Ddi8aiYVV9K27Xezf2ZniLR0bAefcrNXT9om9sZhKbF0_x_PH=w611-h278-no?authuser=0)
3. Uncomment `SET TITLEBAR 'XXX'`, give meaningful name like 'TITLE001' instead of 'XXX' and create it in Include ending with **O01**.
![title](https://lh3.googleusercontent.com/pw/ACtC-3fwyY-HKyP40N9c3EhbvD0H-ccxqIf_Z_MxmDc6tc-5eZ0h3cGuKfW29t2OeyLw101g45JLY4CS4K0Y4nZxNM7d-q7u0i_VteqKNMnCCBTPrPF3P0D_oukJXesZeOZigX02EncYfvT6AgFVkTbMzBH5=w479-h150-no?authuser=0)
![title_name](https://lh3.googleusercontent.com/pw/ACtC-3fOJNoo3lOEkvVqV5WBR86vKtvPTFUlAvTqqJgmdRwPNuNIUVBS5mD35yUT2Gp4O6HbkIOBNeuj6HAzD6rJlvGSI6DyzdR-AukdPBIqv27bhV8urTEnWFuG8FdkeXDLYnlfEM4JnK5l8CGWiy4-TPVi=w595-h163-no?authuser=0)
4. Similarly uncomment `SET PF-STATUS 'XXX'`, give the meaningful name like 'PF_0100' and create it in Include ending with **O01**.
![pf_status](https://lh3.googleusercontent.com/pw/ACtC-3foQVzxpxBK2x_-StrT-2sMtyv1wfkv4MBKPltJmutzuWyYN6SalJlEUc31LTKDOGPEie10-FA6zpgyjIqfV8zDwiNg57FWkzv5mVxrQkHfiKBAnzjKbBCEskWbxYWkeSdnlPW2Ip7SkYBqA6H57Z-V=w475-h150-no?authuser=0)
![pf_status](https://lh3.googleusercontent.com/pw/ACtC-3eQc_SRlNUVxAgsiNWmZFq5t69JwvzAZ4kkfINDh-4esrW5Kgo1FYxijslBgVmnIMQ0aFqG_EfG5zI9p9mrfYrsLcBukGVq7BwxUiSPxHw73450tMkdgtp_dWt5fsbE2wyry0ZzWzcfaoPzOapipkAR=w473-h334-no?authuser=0)
5. Double click on 'PF_0100' to edit the status. You'll get the below screen, Expand 'Function Keys' and provide the function code as below.
![expandfunckey](https://lh3.googleusercontent.com/pw/ACtC-3fA_obE2mhF40CPyRJkAL5noWktu7yw6zMf_pTsnBKubmyiv_l5S4_-4lF4FDX2AGlIZUOI06KBhCXM05ruAETPDkO3RolZv1ZzicZd9_MwdFWZtBmdYQgowsAwrNTHFdZLMM6ilzem4rawpl9iuZWP=w627-h194-no?authuser=0)
6. Double click on each of the function code and provide the **Functional Type** as **E** except for 'FC_BACK', for FC_BACK leave the Functional type as blank.
![functional type](https://lh3.googleusercontent.com/pw/ACtC-3cS1PyKivz2708StkyPE-vqQE8sKW2RIB5NTNa9Bh70iotlct72Us4gM90VQ-KGVj2t-U7N3EVgY8Df3-gfEayNfLm0RL7NPI5fgigrgyp5UUmKRBZqRGBaiI9dR-9nsy3vAakQW_IpwvrdyJNn_boi=w568-h338-no?authuser=0)
![functypeforexit](https://lh3.googleusercontent.com/pw/ACtC-3eOdUJr-AP2Zc9aI-0wsn4WV48imGiW2ajko98AokmIQ98GUo3WOLUKhM-miDfsc3UQ3adcV95_0uhrfpHefbxy1v8rL8I9LGY_3RsIQGIjNE37VXEnpjYcHQF__Eavs7iIa3YBVrOzg1OxZphvjOkB=w569-h340-no?authuser=0)
7. You can check type of functional type by pressing F4.
![f4functionaltype](https://lh3.googleusercontent.com/pw/ACtC-3edxhi_BjEYoCpPd4ZRyoJ69UkFxtJOLXfVy6JbCIso-zQIIGN9_HDPzzQYwGHh3wpQaqSv82tinQlcOSQgqx7W1RC5_gwkecWRNlMqqk5oPVKAGTr28YRzc8iVOnNnFnM6UHHS3EXdXG2w7oqoyOZr=w425-h193-no?authuser=0)
8. Save the GUI status and navigate back to flow logic of screen '100'. And add a module to be triggered at exit command in the screen's PAI. Whenever you press any function code on the Screen, it automatically checks for any mandatory field present or not, if there is a mandatory field then you can't  you have a mandatory field on the screen then screen au