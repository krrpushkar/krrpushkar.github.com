---
layout: post
title:  "Filter BADI"
author: sal
categories: [ SAP, ABAP, tutorial ]
image: assets/images/filterbadi.jpeg
date: 2020-05-27
---
`Filter BADI` is the same Classic or Kernel BADI but with a filter parameter. As you know that the a BADI can have multiple implementation but at a time there will be only one active implemetation. Or you can say that in BADI's filter give you a chance to call specific implemenattion based on the filter value.

In this blog I'll create filter option for both Classic and Kernel BADI, the process might be different but the concept is same.

`Lets start with Kernel BADI first`, in previous blog I have created one Kernel BADI `ZKERNEL_TEST` under `ZKERNEL_SPOT` enhancement spot <a href="/badi-definition">check here</a>, to display simple message, but now in this blog I'll modify the existing Kernel BADI a little bit to display message based on country. 

Open the BADI in SE18 and right click on BADI name in the left panel and Choose Create Filter.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3cE57w_AoRBNOW2f38B1Yf_sfA42ZGokdsahYshlRCX5oc7KQ7ruhMgzmw6ngm-fZe3r-SPvrnOJoS921FHhzMwBXVYS5rdXDgSbG7qZ2f9WZRdTbYxrJwgs42PlX95DGcy6Z4cuCP9iZ-6IrV1Kntc=w1098-h520-no?authuser=0)
Then Create Filter by passing below values in the required fields.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3cfEklf-W2Mfny1xDWzsqAVCCrH86zrFvKX3xJm9xIKAj0YXCav2sTQ2KRyYtogfUGdYOwoXjOZCGr5EqEnjnCssZ35OpQNwYN9jlOdIQaQQjCnU3lpy-iIRPoA5-O_DYHywGUEMgjjzgYnTs02Z1xj=w1302-h608-no?authuser=0)
Click on continue You'll see below screen, here filter type 'S' means string. You can choose between I- Integer, C- Char, N-Numeric, P-packed and S-string.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3eT_XKNSFpO3dg1MuhvPXzSKpzYip6L_Yy68NjGQJqdmYoLrISvkib7DgCDzvp8Uf3wPILbET_pM1Dumg5m72QGi-ipxzKE1eTNSzETSS4N0hFumy409FiT4kyKw4R-FykvnMW_ZOhU5SD3kbgnRkwQ=w1414-h430-no?authuser=0)
Now just create one more implementation for this BADI as you can see in below screen I have already created it. To know how to create BADI implemenattion <a href="/badi-definition#implementation">click here.</a>

![walking](https://lh3.googleusercontent.com/pw/ACtC-3enzOvMesfU-SKN4syBAN6xfz1XLo-raPiKhqOG7Q7yl8YqMmPM3Jy_KG9OpGYmrBZg6f47oFWpyt_zFJSXcr2LaO_Lbn0xC8_p4ty_sP6Hz2KXBSCSuov1xGMB150oS4pB5e9iuVg3294lHMCbThk5=w1294-h648-no?authuser=0)
Now while creating 2nd Implementation give different implementing class name and you will find `Filter Val.` option on the left panel.Double click on `Filter Val.` and click on combination button.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3d3HaSEZ4pysRGRmGSc2W2bCaUBM5XuzapSPnKr5J7nzdk8T1Ozxe1dSJAFB7PbpXt6a9SixhLqaPzdhrIteRlnEqhPw6ZchJLmbr5kIEYNWtrZYqWdsbUy-2iLQzHlg6VhzM3flXM2OscaFvZD_GnZ=w192-h44-no?authuser=0)

You will see below screen, double click on ????.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3fvQgntaxA-DM8KTTOo8b_hirqNnqYXkvozEtVV7rSbfzmOy-gp_gZV-TCh03PmM2t5_gOkjkGF-fF61qbAwnP8-XoyBa2SoLex7ioOJhkJnAJGn7Y0kFX8p8cZ3CEExJad8jTjk9uPwj8SSjuIzmf5=w1440-h187-no?authuser=0)
Provide below value in the following screen. Save and activate it.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3dQBzKRRHX4ZkRmTtd4uFAV30wXucsO4R10nzmLiNaxQDD5bBG0TOiW7ZRvFLvKnETpsW-mXWiUeS41cFF_u976CjAmXet3nNBRFz08cnDo4ypQzTdnmQ6d8vA30naDWJ-I2tHfQdlmf958sZM52bO_=w1034-h522-no?authuser=0)
Go to Implementing class and implement the method, just put custom message.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3dRU_IE1lHrmLjYrwd6nCdVA9GaKMSSnCb6oJ77YMcNx9ffFNiPtqY8r_MllM4529-CcjzIO31NwpaXKeBgAMJ4hb5qYfdhYELa9nv23lAg39a2mXkiYWZ1HHdHlvjBUKVSltgUVHGAOU9pnN0Sn79r=w1104-h226-no?authuser=0)

Similar to above screenshot change the first implementation also and in filter option give the Value country = 'USA'.
Now its time to test the BADI, in a report write below code.

```
DATA: w_handle TYPE REF TO zkernel_test,
      fil_val  TYPE string VALUE 'INDIA'.

GET BADI w_handle
    FILTERS
        country = fil_val.

TRY.
    CALL BADI w_handle->display_msg.
  CATCH cx_badi_not_implemented.
ENDTRY.
```

Here in the above code you are manually passing the value but in real time that won't be the case so then in that case you can choose radio button `'Automatic Through Dictionary'` while creating filter option and provide the object name. If it is domain then select the checkbox 'Object is domain'.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3dOvZ8BniDxYHNZhQ_zgcGPqL1wwotpMcgl_wAbRtYg783DLb3-GtfuN1mNzeGsg0LLh9h8du4Rxql-I561fsGmGSRViGRIgmklWarOK1kXNOR-yduuMsl4ngPbOCzRqPsLkYeN2RR82UIYU_luQiqb=w1258-h250-no?authuser=0)
And if you want to filter based on report program then choose the radio button `'by own program'`.

![walking](https://lh3.googleusercontent.com/pw/ACtC-3ecfuAYQNQ-JW6QSaHXHQBi-cjHSmC-IVcozqeuaww3jADqBV2S_a5Dt3o1S_a_S5HQhWJa31q2B5HcphBZI9KyEDwPr_Pf6iyhk0XSr1HsxSQ8uaNVqjWRNcK200699eIIes0lzUX0V82DtsdINCFM=w1238-h254-no?authuser=0)

## Now let's see about classic BADI

Go to SE18 and while <a href="/kernel-vs-classic-badi#classic">creating classic BADI</a> select the checkbox `'Filter-Depend.'` Here I'll change my existing Classic BADI that I created in previous blog, but before changing the existing Classic BADI `make sure you deactivate all the active implementation of the BADI`. 

![filtercheckbox](https://lh3.googleusercontent.com/pw/ACtC-3fEPBOAdINzGxjEAMM0d6aobVXwbahEQXJTbdp0bZPQAXIVJeFK4u6dZZTyGFpzFx4x0fyKy9K3w69kcfDpmwkygnFVmpICqDEZVe2XTMdYeT43Ay8z_-RfczpY6nvFNzB3ISxXp3_k-wQn2Xn3mPrY=w1328-h788-no?authuser=0)
Provide the Filter Type. A Filter type can be a `Data element or a Structure.` A Data element must fullfill below criteria:
<br>1. The Data element's domain must be of type <i style="color:blue">character</i> and the length must be less than equal to 30.
<br>2. Either the data element has a search help with a search help parameter of the same data type as the data element, and this parameter msut serve as both the import and export parameter, or the domain has fixed domain values or a value table containing a column with same data type as the data element.

`Note: `If you want to call the implementation of a BADI to depend not only on a filter value but on various values, you can enter the name of a Structure in the Filter Type field. The Structure can consist of several data elements that fullfills the above criteria for data element. The structure must not be longer than 80 charaters.

After Providing the Filter Type when you double click on interface name and check the parameter of your method you will see one importing parameter `FLT_VAL`.

![importingparameter](https://lh3.googleusercontent.com/pw/ACtC-3fJreEDb9sAqwoX6QQx_3E9yTzeQEvmcaKg6NdHpcF4AeKsntFl0W2bsFwPcoOU8ghJOffUVH8kv6gZPfjOOHOzmh5jEJyf_nX41o7szrzRy6d8MR6iyBDRphARN8BcyLtO0EGs5fSFZy3YgQP2nwLc=w1306-h328-no?authuser=0)
Now <a href="/kernel-vs-classic-badi#classic_imp">create new imlementation</a> or change the existing one.
In properties tab of the BADI implementation enter the filter value by clicking in Insert row button and provide the username stored in SU01D table.

![insertfiltervalue](https://lh3.googleusercontent.com/pw/ACtC-3dsJnUDtOJ2eMmzVCFFDX7UpBEJ2KkzN9jSJ-UJmRvCO_npaRhPj0_JMZddrEmKDqnxM_ykNxongSzZYsqUonYURO1_GV4AozC01hhd2dZn7YuNRnMjXBnGRoCJLZsYps_Bu4wHUDro4vL-6z5045-c=w961-h788-no?authuser=0)
Now write your logic in the method. 

```
IF flt_val = '<Give the value that you provided in filter value>'.
    MESSAGE 'Classic Filter BADI demo by user' TYPE 'I'.
ENDIF.
```
Similarly create one more implementation and provide different filter value( username ) and Now let's test this in our report program.

```
DATA: w_badi_instance TYPE REF TO zif_ex_classic_interface,
      username        TYPE xubname.

CALL METHOD cl_exithandler=>get_instance
    EXPORTING
        exit_name = 'ZCLASSIC_TEST'
    CHANGING
        instance = w_badi_instance.
 IF sy-subrc <> 0.
    MESSAGE 'BADI not found' TYPE 'E'.
ENDIF.

username = '<Fill the value accordingly>'.

CALL METHOD w_badi_instance->display_msg
    EXPORTING
        flt_val = username.
```

`This is how you can use Filters to control the way a BADI should trigger.`
