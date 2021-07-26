---
layout: post
title:  "Web Dynpro - Introduction"
author: sal
categories: [ Screen Programming ]
image: assets/images/wd1.jpeg
tags: [sap abap]
date: 2020-08-15
---
I have started a new blog series on Web Dynpro for the beginner who are familier with basics of SAP ABAP. This is the first blog of the series `'Working with Web Dynpro'`, here I'll explain the overview of the Web Dynpro components and in the subsequent blogs I'll deep dive into the concepts of Web Dynpro components. I'll explain concepts of Web Dynpro components while creating a demo project (Web Dynpro Application), you can download the artifacts related to the project <a href="">here</a>. So bear with me &#128522;

## <code class="highlighter-rouge">Overview</code>
Web Dynpro is the SAP standard UI technology for developing Web applications in the ABAP environment as well as in Java environment.

**Benefits:**
1. Strict seperation between layout and buisness logic, as it follow <a href="/webdynpro#mvc">MVC</a>( Model View Controller architecture ).
2. Run on all browsers.
3. Can be devloped for desktops as well as mobile devices. Hence can be accessed anywhere.
4. Doesn't require any installation, just run the URL.
5. Can be developed without writing any HTML or JavaScript code.
6. Can be reused. Just double click on your Web Dynpro Component and in the `Used Components` tab fill the Web Dynpro Component that you want to reuse.
![reuse_wd4a](https://lh3.googleusercontent.com/pw/ACtC-3fQC2b2YFzAGzP8F96_sF0nhg7IVIU1WQgj27bI5Pk9Sv3dEY5uBRUpkFpYR7_YQPrE1WlBNbsaDNIVvnW5jnh0S2wFd854kOk-8Y-o9XSvppDfudKNABZMMp8uZ1V-MFwb58ebEHcxpAtC8zIO-VdQ=w1286-h646-no?authuser=0)

## <code class="highlighter-rouge"><a id="mvc">MVC Architecture</a></code>
<img src="/assets/images/mvc.png">
In MVC architecture a `‘MODEL’` means “a unit/section which contains or builds certain data to display” on any WEBDYNPRO Application (VIEW). Models are objects which contains business logic statements to read or write data into database.The models can be developed in the form of Function Modules, BAPI's, Classes etc.

`'VIEW'` is simply a screen( user interface ) displayed in the browser.

`'CONTROLLER'` is an intermediate communication channel between 'Model' and 'View', as you know 'Model' and 'View' can't communicate directly. So 'Controller' takes the input from the 'View' and submits to the 'Model', the 'Model' will then communicate with the database and gives back the result to the 'Controller', and 'Controller' submits the result to the 'View'.

## <code class="highlighter-rouge"><a id="demo_wd">Demo Web Dynpro Application</a></code>
I hope you have gone through my demo project `Student Registration Portal` related document that I'll use in this and subsequent blogs of 'Web Dynpro'. If not, please <a href="">download it here.</a>
1. Go to SE80, select 'Web Dynpro Comp./ Intf.' and provide the Web dynpro name and press enter. Next You'll get a popup select 'YES'.
![wd_name](https://lh3.googleusercontent.com/pw/ACtC-3f3Bv6k-8Td2vsCfvHHyQWzFzaU8_SgWW01ftoeueV1LFEMenpF_SZXgiYPeTM9_pD0CKwPCREkuV_tU91e3TguKFXQuApnLE80aUDc7rCii6x9qTrDDbY_WzVq-Hme_ROSReYrN_dqdPQGyX5mBDV_=w576-h366-no?authuser=0)
![wd_confirm](https://lh3.googleusercontent.com/pw/ACtC-3fk6x6v3_rZK6ZpWIh8SljI2hGNt5dhl_bygAusO_jyksrj4JPES1pHV-LzXkEA17p9w175zTlc3SEzPueswu9sAF2lgwmcMY80i3aVLZnbVh-xTPvNKWXJH3fBLiDEOftk9OXu1mtgS-hl1lp0dc8I=w954-h330-no?authuser=0)
2. You will see below components get created. I have explained all the components of Web Dynpro in <a href="/webdynpro#component_wd">later part of this blog.</a> Once you get a little bit of hands on experience then it would be easier to understand.
![wd_comp](https://lh3.googleusercontent.com/pw/ACtC-3ckL9N8PdHLfhC44_ty6xdws4x25voo3ehMCCPBtlsm6FWnl1Uq5pV3bcBKX9R62wN-IZTiBBdeQCuR0zEuda9GbpstQpp1V0CcpQb4EKOHG_-tP9zMusoqsUtEWqsmu2Pl3bK1wkJAnsTZ5cIdbgGA=w546-h714-no?authuser=0)
3. After this, first of all create the Web Dynpro Application, this would help you in testing your Web Dynpro. Right click on the component name and select 'Create' -> 'Web Dynpro Application'.
![wd_application](https://lh3.googleusercontent.com/pw/ACtC-3c80QNtgt2ZoZWO6I4GnVeNYTzlQSpVZstld3FXyaffLPZM7SVjGNF2HGM7N7uSQj9HF5TJEnqN49z4CPIoRS45DW3qSnnbr3bPQyhU3XXDxs124StXe4SW3hkt5JT2Qy3p74djRCNZ_hz1kmiKSyH0=w966-h713-no?authuser=0)
4. Also by right clicking on component name activate the component.
![activate](https://lh3.googleusercontent.com/pw/ACtC-3eiid3I8cDx6HcK5qK3S9lCoN4LkmC0-pvfqHAOkeuvMfCtINtHY-oXw7AGDIP9I_wpqW3JkgFVfavH6Q8SOorZTHYbA817CknHWTNQcZLyMRwg1V6KbWVHVx-7oVXv312xqzq79rQs_mS1LDPB4AOS=w574-h713-no?authuser=0)
5. You will get the below 'URL' that I have highlighted in below screenshot. Copy and paste this URL in browser to run your Web Dynpro Component. 
![wd_application_url](https://lh3.googleusercontent.com/pw/ACtC-3cx00rdvx5XEW1qlP5Aiw58oK5uuw2wRTJF6h_CSCYqdgq609fFEK1P8a4A1neKOb5lkZNBgAQ1wiwcPEeIBWacvKU7Oturyy92CjllOGsH02q-n8eR03P3FEArCUAy5An2jmsxtbWH34Ez1zyCo7JK=w1207-h713-no?authuser=0)
6. So you got the blank screen after running your component right? That is because you haven't added any UI element in View, Lets add the title first. Double click on View name and Go to Layout tab.
![layout_tab](https://lh3.googleusercontent.com/pw/ACtC-3dcC-PGrEF9cg1fpGUZYyI23bIKwLxTp4s1goezEeeRPCsItkpmViuTJSPYbkTZJz4AKzVCCXCg2VWr0ueGTpT199Hslj6CLbEIOb2ijtuLWLgdNJHZDvtn3NiwDWEupOZjNMVXJ2iF6mcm3nRp5WjQ=w1052-h272-no?authuser=0)
<br> On the right hand side of the screen, right click on the 'ROOTUIELEMENTCONTAINER' and insert a `Transparent Container` and then inside that transparent container insert a `Page Header`. Transparent containers are just holder of UI elements. Usually, related UI elements are collected in a TRANSPARENT CONTAINER. Its a good programming practice.
![insert_element](https://lh3.googleusercontent.com/pw/ACtC-3fhs2wLl63XBgEAdye2fAVsAVU5W-DUPfpHm5-ovryUqFNul1fWaF_a2I7mMgxlICeaXTgeAwOCEynr_mLgml29nP1IKGkMEyOD9rHPDfX4IQKOceP2RnOP7ZGjplx6EGw3msJH8RTE8ickHdEy6vRg=w596-h356-no?authuser=0)
![tc_element](https://lh3.googleusercontent.com/pw/ACtC-3daf5IJ8ACGNAxQxngD-m07q1wb78oUZJijN6I7qr9dFRLoJxfBSZZcLZ3glwMWXxHu0qv1kjxAIHU9SzBbh5Ybvk3Hmj4umR3_7SROlsXiKCbcY5w_5xGUZOH1iJt2MWrxysLxzWuwQtwe6gEXncBB=w570-h222-no?authuser=0)
![insert_page_header](https://lh3.googleusercontent.com/pw/ACtC-3e-MQ_QpD2uY-Q2X8xmbDcWWiMq5XSSLf3-ghat2RiOrwy7y-_Oh9ZYWQTUUe-bGMf5G08Iv_3mguQilXL0SdhZzD6SWmDKVRUDhImY5NwkrfSAGDdhneg64T1VStUIpH7lz5AMY23RXUvJ38LNbUi2=w550-h328-no?authuser=0)
![pg_element](https://lh3.googleusercontent.com/pw/ACtC-3fNbiHuFTlqBi_T4aT2O4RTiG_Eoh9284H9ZzkMjMgI9FGPp87fMiHVNly8oAReTvA2zJ_3bRBMa9xcUvM_9Fj2A1W_Y_vHqQQvri0R5tEKhNKprMr1LuFjPslo9z5gUV95l02a_Wnl8zndpp63Exhe=w578-h232-no?authuser=0)
<br>In the properties tab of Page Header provide below detail.
![pg_properties](https://lh3.googleusercontent.com/pw/ACtC-3czPp0BDmqM_uI6KhpbQ758IApIQWV9VOerUdvU_ODUCjZqQTyQ86yg8X9MVXEW-C8Onpx2rkJp5gtcqc0jnwRCo7WBrUWMiU9x29SHfyShKqIAd7EWOXJyHxjMx1-GMNpZpOb3IddaMNMN3hWO2Rwp=w902-h614-no?authuser=0)
<br>You can either drag and drop the UI elements from the UI element box or manually insert the elements in the layout.
7. Now your 'ROOTUIELEMENTCONTAINER' would look like below.
![rootuicontainer](https://lh3.googleusercontent.com/pw/ACtC-3fKCXDWjlMaLSCp3LrkxH-zsalREE4JmLIhqxncsTx8z57WIP53EvzKfLL7OYwS1MSJ-A_EvRX66j9uzeLsxvYb2MatiPNH-ONoeTkStx20ky83Vqr3DvlBKjZQCLTucr1phjogZEVJH86zS8RkiqRV=w1440-h304-no?authuser=0)
<br>Also notice that an `Interface view` got created.
![interface_view](https://lh3.googleusercontent.com/pw/ACtC-3cyP1Vlb3LaNDq-XpaVy58R4kN4kCFD2KWgIfbvdI7Iy3_AFh2M3XkpA5hKpsn6ulqyjl04HDPggVw7I9jRk4YWGqHoQ_0ehTZuOH_N07vOVRLX90U9Ql7ZeYmZVv4zTdpExKTfMLpyptk0MDvGzz7K=w511-h713-no?authuser=0)
8. Now run the application in the browser again, and before that don't forget to activate your components. You will see the Title.

## <code class="highlighter-rouge"><a id="component_wd">Components Web Dynpro Application</a></code>
1. `Component Controller :` 

<!-- <div class="popup" onclick="myFunction()"> <code class="highlighter-rouge">a. Component controller</code>
  <span class="popuptext" id="myPopup">A Simple Popup!</span>
</div>
<div class="popup" onclick="myFunction()"> b. Interface Controller
  <span class="popuptext" id="myPopup">A Simple Popup!</span>
</div>
<div class="popup" onclick="myFunction()"> c. View
  <span class="popuptext" id="myPopup">A Simple Popup!</span>
</div>
<div class="popup" onclick="myFunction()"> d. Window
  <span class="popuptext" id="myPopup">A Simple Popup!</span>
</div> -->