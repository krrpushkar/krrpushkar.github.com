---
layout: post
title:  "Classic BADI vs Kernel BADI"
author: sal
categories: [ Jekyll, tutorial ]
image: assets/images/kernelvsclassicbadi.jpeg
date: 2020-05-26
tag: featured
---
Buisness Add Ins (BADI) are one of the important enhancement techinuqe in SAP because of its object oriented approach. After the release of `SAP NetWeaver Application Server( SAP NetWeaver 7.0 )` BADIs have been included in the Enhancement Framework and aka New or Kernel BADI.

With `classic BAdIs`, a BAdI object is created by calling a factory method, and referenced via a reference variable of the type of the BAdI interface whereas with new `Kernel BAdIs`, a BAdI object is created via the ABAP statement GET BADI as a handle for the calls of BAdI methods, and referenced via a reference variable of the type of the BAdI. A BAdI object is an instance of an internal BAdI class, which otherwise is invisible to the outside. Don't get confused I will explain this with the exapmle in simple words later in the blog.

A `Classic BAdI` can be called only once whereas With `Kernel BAdIs`, multiple calls are possible. Also With the `Classical BAdIs`, the filter values are stored in a structure and passed with the call of the BAdI methods but with the `Kernel BAdIs`, the comparison values for the filters used to search for implementations are passed when the BAdI object is created with the `GET BADI` statement.

Okay! Enough of theory lets start with some code, because you will understand it better then. To keep the example simple I'll create both BADIs to display same message So Let's start with Classic BADI first.

## <a id="classic">Create Classic BADI</a>
1. Go to SE18->Utilities->Create Classic BADI.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3f-QBupTiWwL7j8eJnzudeCoUo1Y005xfp_3VHM61H9BU2dUmsH0JjIixy_Wf5i1_VhkaHzZoOaPQGk3ZWPSUcJgPWWAVZiMXLl9eDKloQINt0jsD-f9hTr076iMM4F8sgVNTsuDecuBHr0DzSLkp4f=w386-h328-no?authuser=0">
2. Provide Definition name.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3d5f5x1VWu3NvgqbyTiu4qjVgfjNv6eyXgc9jol2hTWxOOqDYbSooT7wyqwudevLZp0eofFenT5ol0QKGu0mVA-F-_w_yCEMPx0ADCMwfn6k1x0uru9lQLoxyLJ2UOiQ4dV3L_5dAqKXbEOOW--b9M0=w576-h190-no?authuser=0">
3. Give Short text and in interface tab double click on auto generated interface name and give a method name. For this example you do not need any parameters hence no need to provide but feel free to explore &#128514;.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3dRzDr8YtoSWTnuF7vU-hbwcOPAqDMxC_kepobXlxD4IEWf_tuvUlIVNajGxaWSyGvvPOg7gLp7a2WZimKBvsrwkBL7pYEIckDHPdjma0iVzEGObBxsu_Y5Z5diH12QgZ-jltA43WJj6U_d3AM16t3n=w1050-h390-no?authuser=0)
![walking](https://lh3.googleusercontent.com/pw/ACtC-3fjZPQukWMbhvH8SHlLuOLFq0fKg9d_TVcR5waY8qZvwVRV_zJsIWpBc3ghKRddPWCEZhpmslMd2WMLnx3haNUfbbrcjcxxvaC21TjMUaYWh7t3rv557wnRwNCC8lpmB2R012hjgORbgbw-FJnkQcaM=w1352-h320-no?authuser=0)
4. Now your Classic BADI Definition is ready.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3dBSrZ1yqjcKnn8v0yzPSJ9MfpHFnbjSatEU-jdgzKeuQEOMDCt6AU2SkDeKOaNOaQM0JceKVOIO96S7M6RSUAeHnCu7RdtF0Q1F2n8LkIgQ_lfSz5CIrXwqb3cm__c9CRfpmT9N-dkMElwxjvDLEui=w877-h788-no?authuser=0)

## <a id="classic_imp">Implement Classic BADI</a>
1. Go to SE19, in create Implementation section choose Classic BADI radio button, provide Classic BADI name and click on create.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3eZ9vjDBRP8c5MFhup6U7UT0Cs00mS9R2fLxB7zQdqIMQhewopeF2Ow0Rm9DTRsC89yypjE0qckUvJQP5LnorrPNb4-7xXkp5acz7osu7pXV8eo3u6fk7iGlBpFwLbluB9la8YoLu_BJE0eqrRb4-56=w893-h788-no?authuser=0)
2. Provide Implementation name.
3. Next Screen give short text and then double click on method.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3fDtrTJKHWiNqKv4hJf0VmDjZo3e_YHWuwFjfQE2sg5eU5S3940uoC7PV1KHzckc8VK4MrBmtFwDmK_mnaCe_ZGRUVPb-MwhZ6SRsPru1XS4JSSjDI6aJG5lrqwsc-crL4jwpsja9pzUs0OB5HjZ-1C=w773-h788-no?authuser=0)
4. Provide the logic and then activate it. Finally activate your BADI and its ready to be used in our ABAP report.
![walking](https://lh3.googleusercontent.com/pw/ACtC-3dJ83tRuyC1ttHidBfm1-e7MMoQgF5OdlMKS_EUeBLvabEclcb45AIsS3WjLL3AzyzwESjejVO4GTaNnCD0-jRaPrOSx9MkvPUY9kwqn3LUA9h7TGNR-WV4zq8OiXjI314l-PTUHMlYJjNcyPbPo4Yw=w1114-h252-no?authuser=0)

Next I have created a Kernel BADI `ZKERNEL_BADI` inside `ZKERNEL_SPOT` with the help of my previous blog on <a href="/badi-definition">Kernel BADI Definition & Implementation.</a>

![walking](https://lh3.googleusercontent.com/pw/ACtC-3fxPDbvfUxvcMN1keIhFGG331BMvw2Uc7ra1ud93q8GzJd3Eq6ieV4J7PpSNZPARsHGQbh-om_Rj8HbyWJbl39kL4CWYxYC8IKFh_OKGT-hNGyO8AYHpolM-CW_EnzFwTfASoP7P3NY1fE6mukssK03=w1332-h516-no?authuser=0)
And Implemented it.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3c0Y3BSa7gtpb0-V7kjAb0HdoWxMmczU8la6fNfH65nz-Ge0OEla20g-iU43wrME7LBcEhNf8fmUq-nZ6mnn2N9r0vkC03eYLaH_CMfuvc3VcWTFDgcGfrq7X31SrvsNX_MF-pVOnceQPrpWFfYoG_V=w1440-h439-no?authuser=0)
The logic I've tried to kept same.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3cIESajhV38zFCt7HBSwEm6NOFY24AMKF89YWn9_bQgVTWh2AAiHrpMhNIEvqf_Q_FjrmBNdxdqvpeU1i5yf9e2hebNBNGlBWymkekgI6R9wdLi-4LmTcOu6EB7sA5wGy2MZrJtWN34LKEze3IwR1Ee=w1118-h230-no?authuser=0) 
<strong>`Let's use both Classic and Kernel BADI in Report and see what happens`</strong>

**Using Classic BADI in Report Program**

![walking](https://lh3.googleusercontent.com/pw/ACtC-3fJNrc6TJ1Sw4nyOBmOKTusGWPdQm2NvdD_YLqeyOtbqUJDFLeIDjl7GbqdHz3FNR3A1sJ62F4MTCG979MGjvOOl8QdrVDi__zFAAl6-gYOFMldMX0l_wSR0O7FKYRSqB_BrEn7WOKh9HSz6jXzrSio=w929-h788-no?authuser=0)
**Using Kernel BADI in Report Program**

![walking](https://lh3.googleusercontent.com/pw/ACtC-3f19a0qNG4JFDPka0uwMQUiEv9sQCX63Ht8bLkAs5b9WMiKF-VpbvjY-H5E7QRFoW77_u03DKDzbrqkYivhpIlvuin8gFOIDmgS6c37gqwGm809wQnMAP1S5_yxh22vMlboOL7CP6vqpUk9zTXEU6Fa=w1023-h788-no?authuser=0)
> They are called Kernel BADI because their handling is done by the SAP kernel via the `GET BADI & CALL BADI` statement. Hence **Kernel BADI are faster than the classic BADI**.

You can compare the above two report via T-code STA, run the T-code and select radio button <i>program</i> and give your report name and execute. Then after you executed your report press <i>Back</i> button, you will see the Runtime analysis, just compare the time taken by both reports to execute. And see for yourself that `Kernel BADI is 40-600 times faster than the Classic BADI.`

Maybe you want to Explore Filter BADI now too,<a href="/filter-badi"> click here.</a>
<!-- Education must also train one for quick, **resolute and effective thinking**. To think incisively and to think for one's self is very difficult.  -->

<!-- > We are prone to let our mental life become invaded by legions of half truths, prejudices, and propaganda. At this point, I often wonder whether or not education is fulfilling its purpose. A great majority of the so-called educated people do not think logically and scientifically.  -->

