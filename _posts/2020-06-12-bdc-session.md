---
layout: post
title:  "BDC : Session Method"
author: sal
categories: [ Jekyll, tutorial ]
image: assets/images/bdc.jpg
tags: [featured]
date: 2020-06-10
---
Session Method is another method to transfer legacy data from flat files to the SAP system. Other one is <a href="/bdc#call">Call Transaction Method.</a> In Session Method, your conversion program will read the legacy data and store it in a batch input session. After creating the sesion you can run the session to execute the SAP transaction in it.<br>
`session :` session contains a group of records, which has to be transferred to SAP.

### Properties of Session Method:
1. It is Asynchronous process.
2. It can transfer files containing large no of data.
3. Hence it is slower.
4. After processing the session through `SM35`, database will get updated.
5. In this method, error log will be generated that will handle the errors.

## `Diffrence between Call Transaction and Session Method`
<div style='display:grid;'>
<table style="width:100%">
  <tr>
    <th>Call Transaction Method</th>
    <th>Session Method</th>
  </tr>
  <tr>
    <td>1. Synchronous Process</td>
    <td>1. Asynchronous Process</td>
  </tr>
    <tr>
    <td>2. Process only one transaction at a time</td>
    <td>2. Process multiple transaction at a time</td>
  </tr>
  <tr>
    <td>3. It is Faster</td>
    <td>3. It is Slower</td>
  </tr>
  <tr>
    <td>4. Used for transfering files containing less amount of data</td>
    <td>4. Used for transfering files containing large amount of data</td>
  </tr>
  <tr>
    <td>5. Manual Error handling </td>
    <td>5. Automatic Error handling</td>
  </tr>
  <tr>
    <td>6. Database updation is Asynchronous or Synchronous</td>
    <td>6. Database updation is Synchronous</td>
  </tr>
  <tr>
    <td>7. Background scheduling is not possible</td>
    <td>7. Background scheduling is possible</td>
  </tr>
  <tr>
    <td>8. It returns SY-SUBRC value</td>
    <td>8. It does not returns SY-SUBRC value</td>
  </tr>
</table>
</div>

<br>So in session method there are basically 2 steps:
1. Create a session
2. Process created session

## <code class="highlighter-rouge">STEP 1. : Creating a session</code>

To create a session you would require 3 function modules.<br>
`BDC_OPEN_GROUP  :` It is used to open a new session for adding transactions<br>
`BDC_INSERT      :` It is used to insert transactions in the open session<br>
`BDC_CLOSE_GROUP :` To close session<br>

In this I'll use the same requirement from the <a href="/bdc#requirement">CALL TRANSACTION</a> blog i.e to create customer master data but using the session method. Most of the steps are same hence if you have not gone through the previous blog of BDC, check that before going forward with this blog.

The first step is to do the recording which I have already done <a href="/bdc#recording">here,</a> check it if you don't know how to use SHDB. 
Next step is to create the report program you can use your previous report that you've created for Call transaction Method. This is the benefit of using OOPS ABAP &#128522; Just add 3 new methods in the report, for me I'll add in `ZDEMO_BDC_CD` and implement it in `ZDEMO_BDC_CI`.
For session method our calling will also change as below.
![session](https://lh3.googleusercontent.com/pw/ACtC-3eeFuNvqzmM46G1O1FBknGXHlt0fV5I-kS3H1qtRFDdmwHYkKk9aXHLZnHU9n-MQMExMVt-k4Ak_boOzPLXRxqgFcgpYQUnhYpxxPH1V4A51oC8sC00P_PFVO7xXHwigGfVBkdC4xlRYM9w8SGq22qv=w1040-h626-no?authuser=0)
**Class definition** as per session method requirement, just add below methods in your class definition.
![sessioncd](https://lh3.googleusercontent.com/pw/ACtC-3e-Dl5NFeGEGo77fTWP88gPxawOJ47-7BcgJrVP3ZN9CkLSgB_SltT1VPXvQpfHXcUIKttinXn3H0ONzZk_caOiUAr97bIUiq_FOaeXou84ummIZMSbgfLQDIlAuf9V8zwSR9Sik1U9574LLD6mN0Zw=w561-h788-no?authuser=0)
<br><strong>Screen UI :</strong> Change it a little, just like below screen.
![screen](https://lh3.googleusercontent.com/pw/ACtC-3ev-sasnkAQh5rUNmwobhy7olMwYcAIPJtL8m2LWVexE1bkbshjxIGqslO1YiVD2mSgmW-G_ADPl9S7sNKcqC_M8Aez_Oh5kEqhyiMm_KQ5n84F1kIRJtrhaqLkxunO8BruxxmwhHSDpXyHSXpIW1K9=w1054-h626-no?authuser=0)
<br>Now implement it in 'ZDEMO_BDC_CI'.<br>
**Method 'OPEN_GROUP'** : when you'll insert this method in your program using 'PATTERN' from the toolbar you will see all fields are not mandatory, so while calling this Function Module use fields according to your requirement. 
Here I have provided 
<br><code class="highlighter-rouge">GROUP</code> : session name, 
<br><code class="highlighter-rouge">KEEP</code> : if you want to retain this session after processing, 'X' means you will retain it.
<br><code class="highlighter-rouge">USER</code> : user who is creating this session.
![open_bdc](https://lh3.googleusercontent.com/pw/ACtC-3c_7QaPwEucZjZfwSAQkxOHLnesvS89tFnFu42mA51cTejj_tjiZGzoXNvSVWvD2ZQ2r9bZ4wZRDHUzJYRAq70FkEh3xr___X69Gcfzl9npRqUpI3Q42B45LsXS96zw7YrV0eguJqMhirbHCccNch_7=w1030-h364-no?authuser=0)
**Method 'INSERT_BDC'** : Loop at legacy data and populate it to BDC structure and inside the loop call Function module `BDC_INSERT`.

<!-- <div class="highlighter-rouge"> -->
<!-- <div class="highlight"> -->
<!-- <pre class="highlight"> -->
<!-- <code> -->
{% highlight ruby %}
LOOP AT IT_CUS INTO ASSIGNING FIELD-SYMBOL(<lfs_cus>).

* 1st Screen details

    WA_BDCDATA-PROGRAM = 'SAPMF02D'. 
    WA_BDCDATA-DYNPRO = '0100'. 
    WA_BDCDATA-DYNBEGIN = 'X'. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'BDC_CURSOR'. 
    WA_BDCDATA-FVAL = 'RF02D-KTOKD'. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'BDC_OKCODE'.
    WA_BDCDATA-FVAL = '/00'.
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'RF02D-KUNNR'. 
    WA_BDCDATA-FVAL = <lfs_cus>-KUNNR. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'RF02D-KTOKD'. 
    WA_BDCDATA-FVAL = '0004'.
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.

* 2nd screen details

    WA_BDCDATA-PROGRAM = 'SAPMF02D'. 
    WA_BDCDATA-DYNPRO = '0110'.
    WA_BDCDATA-DYNBEGIN = 'X'. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'BDC_CURSOR'. 
    WA_BDCDATA-FVAL = 'KNA1-SPRAS'. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'BDC_OKCODE'. 
    WA_BDCDATA-FVAL = '=UPDA'. 
    APPEND WA_BDCDATA TO IT_BDCDATA.
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'KNA1-NAME1'. 
    WA_BDCDATA-FVAL = <lfs_cus>-NAME1. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'KNA1-SORTL'. 
    WA_BDCDATA-FVAL = <lfs_cus>-SORTL. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'KNA1-STRAS'. 
    WA_BDCDATA-FVAL = <lfs_cus>-STRAS. 
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'KNA1-LAND1'. 
    WA_BDCDATA-FVAL = 'IN'.
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.
    WA_BDCDATA-FNAM = 'KNA1-SPRAS'. 
    WA_BDCDATA-FVAL = 'EN'.
    APPEND WA_BDCDATA TO IT_BDCDATA. 
    CLEAR WA_BDCDATA.

    CALL FUNCTION 'BDC_INSERT'
        EXPORTING
            tcode     = 'XD01'
        TABLES
            dynprotab = it_bdcdata.

ENDLOOP.
{% endhighlight %}
Here when you'll call the Function Module `BDC_INSERT` to insert the T-code in the open session so pass TCODE name(e.g 'XD01' in this case) and in the `TABLES` pass the table for screens of a transaction(here in this case it is it_bdcdata).

Finally close the session.

![clodesession](https://lh3.googleusercontent.com/pw/ACtC-3cEb4duH_rrzndeaYxmCnNuPtfTzgSw6l_JAfwdP-US7vP9ZPz4pD2gTplTxRlkyKkto07n9jEP7sXsgUydKUVPXpQU36ag22SeRgyuLuC0cdVrNxMazb_NobTSfKngbRggauBWh7hQqjwLIv5R3hTd=w1032-h276-no?authuser=0)
<br>Now run the report and upload your file, file maintained like this. Just before uploading delete the 1st row and do check if all the data are unique.
![file](https://lh3.googleusercontent.com/pw/ACtC-3cZuO4jF01kva2-aUhdHYj5T1ZXKWG3TS6eJBV4LktN73yGfGwDb29EnxdR7JxTVvUa6JlZgzhcNivnxO0y1XOP4u77t2tE3laMuhORYxyl_xyfrAViP-4b9qlf2Rc7XBlo0T4edgj74NTU0BNkr90O=w570-h212-no?authuser=0)

## <code class="highlighter-rouge">STEP 2. : Processing created session</code>

Now go to T-code SM35 and select your session and click on 'Process' or press 'F8' to execute your session. If you find the message `The requested session cannot be processed` then select your session and click on 'Release' and then try again to process your session.
![processsession](https://lh3.googleusercontent.com/pw/ACtC-3fMFHQJXiq4ybngrPUEJJTAwgqtn1Xo6OXhv4y5JPC4NXWG8VH-0xlQ3q1n24Y_SOEkiC95ENqRLip3x0TmmZaiqrJMiRlZRJHXBb0kbB7cQOcQgXI4GAdjLBXZ2i7rRv5J3I14ooBOwx_tbbgl9MEv=w1440-h359-no?authuser=0)
you will see few options to process your session. The radio buttons are self explainatory here. Choose mode according to your wish and click on 'Process'.
![processsession](https://lh3.googleusercontent.com/pw/ACtC-3fOpTF3ahwwbdPjL9AsdDDVqhj2EMv2kO4DtvRecethqH2Su2COMaN_zp8Pn22HGXQod4kY1DZXG-AkPJ7SrWY51aDM1OSlbkE4-ZPVHrnxQVpIt9TTo3oGkCbV49CS9jzsT_n03VfZ5yruT8QTmOQI=w982-h482-no?authuser=0)
You'll get below message.
![message](https://lh3.googleusercontent.com/pw/ACtC-3dnF-7mKdem6J7Iwo3lynb9bZKzuWDY-tIrV68D1GAiwBsO4VQzIBeTZmiD6SsOFbzjF_-yU0zfXAZxwqYFsGg7JTve91XRt_Ekwe9cwfevk-yKOUj7jqqgxyych3pyEaXjHdMcyZa9KfqF9XjnuFVh=w870-h270-no?authuser=0)
Click on 'Session Overview' and then double click on your completed session and go to 'Log Created' tab and there you can see how many records are processed.
![log](https://lh3.googleusercontent.com/pw/ACtC-3fJ0ZmPCIaIeZI4dwmsIDPrGu-m1_2ipONvFs1MDcnVZrEz_BXSNaohbTjn6m6wrXHLPAyPDfxdod2iKjoIb-ivJhWN49KSw8GulaQnox3aqcgoJSyhCA0k8FBmUteyAyt5VBC6rQi2kjiuEodT3VOU=w1034-h468-no?authuser=0)
To summarize BDC session method, first you have to prepare a file and upload it then using FM BDC_OPEN_GROUP open new session, then using FM BDC_INSERT insert the data and then close the session using FM BDC_CLOSE_GROUP. Finally process your session that means updating the database by executing your session in SM35.