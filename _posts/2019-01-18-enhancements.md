---
layout: post
title:  "Enhancements in ABAP"
author: sal
categories: [ Enhancements, Tutorial ]
image: assets/images/enhancement.jpeg
tags: [sticky]
date: 2020-05-20
---

Enhancement represent potential customer requirement that have not been implemented in the standard software. The standard software enables the further developement of such exits at the customer site, using logic specific to the customer.
Before going into the Enhancement lets understand the difference between the <b><code class="highlighter-rouge">Enhancement and Modifications.</code></b>

#### Difference Between Enhancement and Modification

1. <b><code class="highlighter-rouge">Modifications</code></b> are changes made directly into the SAP delivered objects( also called core modifications) Whereas <b><code class="highlighter-rouge">Enhancements</code></b> are additions or insertion at predefined points in SAP Objects. 
2. Apart from the definition the main difference is <b><code class="highlighter-rouge">Modifications</code></b> are overwritten during SAP Upgrade or application of support packs and have to be reapplied/adjusted after the upgrade but that is not the case with <b><code class="highlighter-rouge">Enhancements.</code> </b>
3. <b><code class="highlighter-rouge">Modifications</code></b> are not provided by SAP whereas <b><code class="highlighter-rouge">Enhancements</code></b> are provided by SAP.
4. In <b><code class="highlighter-rouge">Modification</code></b> you'll need object access key whereas in <b><code class="highlighter-rouge">Enhancement</code></b> you won't.

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
          <li><p> There are various ways to find it but let me tell you the simplest way. 
          <br>1. Go to object navigator( SE80 ) -> Select package and put VMOD -> Press Enter.
          <br><img src="https://lh3.googleusercontent.com/wBviub-g8RSLrZozMU-kPa5pqeanHy7Fi1AN1TkmqVZvUleHgq8Tk5GpmIuiz731s4LJlTfLNvwMyeqPwr_y9R_sTg4P__Jb7_W6XHAPFdMrVFGWMFkk_-AU9Co-UtVEZfPcIbicQIY8zUJ8BNtFTz3Hvo2j7PbsJaPRgtz7KQxwzoJKBYLb8mBHFLlh0M1mFVqV4gU6P-RNkak2WtlX4D15lyx8LKJsDJ4K4jZwlszCCv_g-aa1ri2Az4lXMaOh9SfCq7XRSycLN40hFE5R2A_-Gse_oC4y3J1zN_LgrdCsimsRapd2mOy6QRdSsAygvXeVuwq_fqlXGkfFMd-nAbR9zZ8hZ8-j9aL5CkSt2FjQPms69HeluH08F_-Bs3xB7Kq8MFJmG3duYU7TXrM5x_It_BodRkuV9f6N94L3hoQssjZ7BlU_qSBXNB-nDPxvvkw4MCfrOjvhx2V2tNrT7qbstAQBr0MYzekgAppD68jBwGJlC1jkuQ2PqugRtPnu51u-L1M_dDsCmHLcefVwthXV1lWlLPD01DaHwq0pW0y4w55ej5pW9O08Dobup-z9tukqBrX5WSM-GbZL_beFCVGHroVy-smJlRANLNyLLUdMhCkGGmjLvtQR0CTWUKIJhnu5bKAmUppFZ5GTlfZjllpZwZdue93iNwNwskzZrtT-CbgLN_MMzyxqaxv5=w524-h550-no?authuser=0">
          <br>2. Choose your include name and double click on it.<img src="https://lh3.googleusercontent.com/LQNN-gp6Q4raHXx5TKTCUVtDniG4H7DvSB02b2q37hSah92EyC2sMV5FXRJ_hWwkkVYZDcw1wTO1c20Vm7SFIwf8kWJXIx3KGZGApjJO85u_eiX5-rimK1OoGbm_Pd6DXfQRoU5rx7Ehhfqax4VmTaNUPMc5x8DIAClTDUqiR-_UI9tiZeN0JZHpy76Qvz2IfHHzMhzcUAVl8GNtFQ5jtCUcpG5oEMKm2xTP4XJY1VdBKuh9rFyYcywo2ZtG_F5Vs0Ioz23plOX-HCYUICSW0smENNM0pqRzPD3CTagkbsIpG5nAbTtmg4Nhtzi9fVNom1kjomYCmvYIOrcOV4BOj_1pJixYFEFvFq_kiU8PCu7XFGChzVLJ6M1vfU9s6tl1dsHeajWgbLfbtXRxdd_s3udM6EyzI5YI3HPloj0Te0l0psRMEU4R45TSz-IoaiRHvviekJ9TByUljOEO0C5GdYB1-38vjh-exvyQbFcZSl13ce-xsIAx2xm7VHB4laWcBzsouHJoDg2t4VudcJQ92JfGBS0yJH7wyzN0gRwV6-J9mjnZBzJZpqbjw5nIZ1PWE_rNB7lAdpmRIcbtmyxHVR-MKnlttgXO-WFe5Tw7Mb_c0nNbhkSpB8_-Jeytu9IIxmMl6OuKoo1fTsMJQg6fic6oRAW0YceNxCp3LmsUukZYUswVBPLqcTDV2iwo=w399-h788-no?authuser=0">
          <br>3. You’ll get all the list of the user exits in program and go though the description one by one to find the right one for your requirement.<img src="https://lh3.googleusercontent.com/MjDWfCf111iNKyCGMZTZZ9u_NPx5ZQu3diTh0SOTLK-Z59doOUFVAzVFEf3dtP43Z3mo2oaqkdJ5TmhDnuH6wxbsw7rzkyLUESUvv77nbOy8UP4Ds5cPmJNPJfEKzR5D1ctCMhGte3YeiRyb_nbOlPwoOxoGxgTPdi7qSvCLDyZ3RKe_WoymAxsILWPPgs-P3ce8GSOorJcxhxqFz2Ml3G7v9zNaqVro9XeEUgdJLagRVE7MB_5kbeWx0xSeHvQ449HOG4r1f3FfC8G6uu5b6R3727Uixaz7LQlwwKYfP_TEwzl0TUzgM4dUuW33EwNxokiQ61iinrUEpQ3sX3-vanajCNGADz-Q6r3uYeov__o-dRjSKxpyzGzp2A7Ul5CeWLVcaXO5_vWJAZVzekk7VqEA8nJQ1dxOOEo2KLCBw2TH7IbRGtSf5jWqBYN7eVH2Xlrl1U5l1pgGvrlCnvpUOdY6wkEyzCmkF3FmNLqwiJaahfckqGDYMNqPtplPPXHL1grYGf76B0e2Dy8kuLwDkV5h-2rbZFf0hVVjjNzqUUVfa2Q4BlIKBu0EymA_2fEXvwNOtO16tQgz_H-0hsGCwHQYHWQhGXQioLPn7R-SKRZzpyMfvNA4ohQ0hhMyY0KnOmPzqi7KGhNZm-m79F8c8C35stZewiHiAs5LtoxV6TEDKAh5GP2d8kTPMn8w=w1440-h779-no?authuser=0">
          <br>You all must be like WHAT! how are we going to find the right User Exit but in my defence I already told you that the Functional people will tell you the name of the User Exit for your requirement &#128513;  
          One more approach to find the User Exit for the given transaction is:
          <br>Go to transaction (e.g VA01) -> System(In Menu bar) ->  Status<img src="https://lh3.googleusercontent.com/vQdcuF9ZYG2uMQF4Cpb3J3iwHIV1jfg46M9sFhNHguGY-0jpSVP9Z2-y82ap3XifdXnpBetVA438xHmXWEp1rWEru84k1KbveuMuSZ2mhcJ9U_EHW8q0RG6QQo75YWkPEC2ysPZe6KutCFtoBqmASFnQ1yCBPEJNGfiVlSuXkCf72M3Y4j0nogaH9C4YSK-H7EObBMKQi_lGur3Dbcl2BjLyI5kznh69OFHclF99GB5EiKPggA4T_cFFlUrAp1WWuNtJe91AhpkJ1AYG77SXkKn62MKQ_lTVgjHXhRoLf0cMozqnyck9IhomI9mNXAqOej61Wzz0cWDZGLUt9JzgWpB5aLRY2_r9fPVzFI9-WnQxIdFP0rjgdtw8P6BwyzdF_Bo3hxbGs1b9xO-5hyFLSzSiLpO7p_n9eATmb-VssdMMQnaARM3nN9V44jFp3PtrSl4QAklRsk3wSJBkCxOLCPWqX-3ZAwNQyCZ9MLZb_DSdlz499gKMvlSl2I_MosJQNLERwgubz9k4YHnwAP9aaKEZhf3HdyaFsaB4atkusoGB3OBjvXeoWsguhN9nuMNXEpfmoj7usOyH030BUZjWs00oYyy4kqPmO6gd2YgF2-d9jUXNMZn_bSO720GTs9hASxtUVl15hGgyLUR5a0y3I7hfEnpOa-TzKa3FpG7aniC46GNYV4Y8VXgLKref=w926-h736-no?authuser=0">
          <br>Double click on Program(screen) name.<img src="https://lh3.googleusercontent.com/uHBkyVVi0_zENsm4elZvI52ihyzRcUXdDGB4m9-8Mkwosarf0XHogWzCnS50icSF-CVYRTDh74x-ZwRJjU7nfsdrB5xlHhwFjbkzxZkSn2M4TeBxh5_Rb9Z-Cu_lxGlBAtFDa2_8sqTPEyRcgr0jqGbZWAeE_EYXmxs1fCRBBYZhQdK5UGb_e0nJM3dnO7BLp0KmtNq6GBi-NVfObmQto7WNYPW6qmtnuNvzPZeCf8IFSl0Ez16fw-nAdEjqxAysJYhW5ozFMwYz6RU05-NGWVm4JMBOdcjiCgfwwrJfu1dnKwmwVQ7VznOoI9sikcznW664wpfzG5BCNvvKlOGMXNtJlvod736AlpVPhfr9bbnKxOWQMBL1zThleWTyJXzJ0YkmjmRpsvdUC8aKEf2mKlaQ8xWIkEymCAWWoBdWrFyTlJzjoE0L6AOqu4hBmWu7NNhNuppMMH_2GHJFpdRsaGSo3Hr63JgOEL33OczkAH79Y4_U1f5lr5kMP9i1nS2XaMcokkErkmF2nFfmkMS-w4cC93KYTupTLwUcSdvcJFXAuidHfEUfU9U22LJUiGzeLLHjh6letAN-jHty30h5TLP85-fYB5ieKyPTWRFfPyQozJuPladWW713SD7o0tiRdxBNEXDn4kX6zIZbI3aZXIIuVkdE6bQ8aJ6GR-S-y59RivpPzKhFv2AwK08K=w1176-h721-no?authuser=0">
          <br>Chose your related Include -> chose your related User Exit.<img src="https://lh3.googleusercontent.com/Q_JQwwqpbHPi9nXzhoEjNT58XnOOIOPHZMHu-QXjd9zS2ubp_FE45O65e5nwrOeRuczeSEnalUpta1xfax3cvH7ml9trfmob3jBlhFr33bZUGI_j5oXESQ2vPbZVUyGPwjXJ8kAWNl7KMkvWKR-2dNagy1wZu9D5r47aUswmsLZ9Q-OVqBaBdtJ_QbWVDVWx_-l96f-hUjaGenudsC_eGLbuHGAyJkS0urzoly6xa0bo97opYZqXmRo0aJqfn9iG73VcfoN_WjasMzglXyazypkbKRKcC4r5WIxhcmV458L3X2oKe42CDaGcqYZfHNCCrUoEZOf77rq-CTE8xjRhIv5mKkdC3buDQCia3KG5GO_M4Y5gRUqLyjx40pAsiBR0IMSLt4UFYF1c8hTn2s8BcC1J6PupM-PxjfvZ7tLGbhy4-G1Pxn9phTViwgZLrhcVo6oBcu7iwp_wQnnurYxq_3qnuQltC_rIS6-Xecwx5P_0X6yzwXl_OoJTuxy9B_ytWCBjiQdh5hIpxoo19rxObXZSHgD0fsI5PosfxLjLJhM-IjtH_FznChN1Iyf7iZWoFqoAPMm3ErcAihYe3COAgtXMSUKEY648CfY_HHJShOJl9EFZXvfgVa9fnrANPUqZftIpuhtdR4w7Dt-kf2jEDV02TXO0zsaUl0K7AUI346lyokhIeEWEozXtu-ql=w832-h788-no?authuser=0"></p>
          </li>
        </ul>
     </li>
     <li><span class="caret" style="color:teal">How to implement it?</span>
        <ul class="nested">
          <li><p>1. Go to SE38 and enter program name ‘MV45AFZZ’ and click on display.<img src="https://lh3.googleusercontent.com/HIa0JFWZcTA6eG3U5Gql4kIq4l2D2RpliTXNIWhZMIiqMA5JOjNsHmHGBqZLUg6vhzJ2voVQJrYq-99T-msh8jDV9d2_IcIkXvjVqlhQ0GanrvNGRLMP0DlOgtAFgIo6clUW3BnTJ8RoAn5rK49rMs4ThYr5amn4llj18sx28U4ejXu-LDzRRVJtvXNJ7hATgQQlqmOc1QMrOq9M1o-8dGMuoqpHK8OOxSbKJ0WDW4Fb7BaL7tTsMtva8Nnt7uQBjics9YHUuswRKDO7b680N-dpXwjWwviVodBPCcqo_fotCwbyByKsfiQjEKOfPygVt5DkjzISDoCaZOaY7ycfgrJPK5KCTUu9UA2v7ncSKS-fkbWNmdl30by5Hc1VR__ZaKCPwx_ioeaczFZdulZiKvBYClAgPaNtw6utiTmHmhWAw_0bRQmqFxD3A3AnbdAtDxTergdL728rqH-x-mLbUMCIlKrXMzT7fGk0Qce5Vq8DMDca-GleYppdiPqN40swqEWJkCNAb1ZLuFM79_86Jd4GiVgICdXr8YkGqTzJFDkpmOr9cnNLNPf_q6C7kWQECoyw9348bH4ib_lCHog-z-Tv_YxstObbksT7EbPHYHJqd4dvM5IQlC4o1b7j9kva5c8k_cgfy4pJc0Iti0eV7QNdW953vkZTp3fOgtaJgUqtAA9qfFB7ehT9BqH0=w966-h688-no?authuser=0"> 
              <br>2. Click on find function key and provide your User Exit name and press enter.<img src="https://lh3.googleusercontent.com/OIK6mM5rCLLCL1lzf6BQA8KU-4g89RmtQtPWjaUiTes3egW5ZeptvPCoYZ2XQhuQnl_vulO8Kf7r9s22ZVMMK0N5VRelM1rX-20poqtvNw_9F2I-TlwJOzOvZlRRcCfGdzIPT8Lwr8sGD21we7kLFfww6Jxjb2tVmT7TwDDI1vJ7vZyx99wselGxJqTEeRLkfpoTmu5YdJkYU6QeTGQcxPalu0fE58khWFsPgTQA11FSotYBPjoAiYpsvuVsSCCNimam8vREEsc7fzTZFPtZ-BlBUvvZTUnUc786JpJzdyp9D9z5bT08aRGPCQx8g40fNkzG12ijg4V-f6xUz6xPPnQhUCvUNJ9BlV_zHBsqkGkVmven3NkanAfMe1bufXEBO_rF70LOe8X7h1iNP4J8vxn-Bv4OOdsiMjVsq7HDtqQYYGfVBhYKYC8nGRQZSW28KC1VCHndG1TZzklfbzojECgub1y9uwXdYjbG1G39vNvcTJrHWhWQcAEtSaz0UnJytHRI3uS2u2vO5FOka1SNqvGyX6ELBxEht1gryXJ8fyeYFHmEoCK6b-dFmA2-ZRpktpeF5Hi8HT-S1SEMcr-W9QKXSb24e3FJRyEM5bKyYbSY0gDsiaIYigLdyms1kvDU7sGJbfFkV6zUmb0BRM0b0ZcO-EnORiFTv2-FR4OqZGwELJbfPNdes9XiZ5cp=w1094-h776-no?authuser=0"> 
              3. Double click on user exit or form and identify the place where our logic should be written
              ( this is ABAPer’s job &#128513; ).<img src=""> then Click on enhance icon on the application tool bar. 
              <br>4. In the menu bar click on Edit -> enhancement operations -> show implicit enhancement options -> 
              It will provide the yellow line for all the forms.<img src="https://lh3.googleusercontent.com/zui6NzIEIzZjqD8VKUBkrMQq9CY6bnmzTcusw9UJ8WsPIismNoJWvnX54-AHRN9Moj3OP0hCR7ye5VyvXj1KoEo_6kLt9WfgIwwcSSr_NWtkangbJN-4dH66pQwLrItK4p5qC_4EKcE1YkrjgN7v3fX0ixLU7lSdlsHV6EOMLqLO-oeZOR4xbfasKQtOspYge9NLuTaR_sXWGHBNTLom_nLV3xWvbeMDo3-s_gnYjDjSN1iEopdV8r9gMLoW8hnOl19ZJ2l9ikfPA3Ayb-zzIB-AI5bEazyaF9NzBE4mK09om2cmbQlKuT0wMnr9wnlJAuKOrflmQEX7khdXw_zOTorsyt8VDkbm9x6XhSxcFo7y8Cp7HhvrDthmEoHoqa5gIh9MruUtIHnw-iV-7x4BrEtiweFLh1gMvQxVSABSs9lhtBgGOGvdboa-uY1do0fUXAp03CL9XKey5u0sSFJ_uuyno-ULXP3-hVjToSk1vK-m_luZr6Fr8XAygYYxCLfI1cP-YndzpnvwMzdjmrC1BKnN_2cl_tNRh8Gp7WeJZZbxC-R32UObnTGZSaevSvJAtuuEijJvN_S3UJ07wLZCMEd-8tFttNIj33SVVe2ojCUi4Y1nPAvjQPcAFuaN3mGt0HOi3teVLdf1w1yxjBRT5JqAP83BhZaSQbsQQk7XAjs5c1P3UZm0aAwMbMW1=w925-h788-no?authuser=0">
              <br>5. Select our user exit yellow line and right click -> 
              enhancement implementation -> create Implementation.<img src="https://lh3.googleusercontent.com/eOskYPltt5RjoeRf0J4kB1sP3WWl8hWUdk6ULVTINvLWwbKpNX_J40NObgTSDxfnTbyTvHHYBd-qgQftnvYsBJSyTXuCfjxE3jnfXMqoSR7umvE2w-wgPYxfs3pMaS2abt7zevQIbks0TPhPqtmVqcTTOpD3U7Vrn-0HyQT0ExKTHHz-Wtgb_gFQ7PF6gzY9hr_70fUJJFSG3sDP4iK9GkA9nTKr3ipvFgB1fCkWVlYiWYSO5m4oWg87P6p5g18s3B8ari3JUWJh5Mwk7Zp3fC-JVHG4oEgQn_1t-3vs_GFC-KjiEOeaY5bB-RJbMRXG1QjhFgGGWHPwCMi-Q5dRkMKTCwIh2qjGQ3BaSQxl4-7EWV60l92pUyEn_IDtEZmlFNeE5Xa9_so6aPCltFUM7cMS9WM-HhGs40LoJDjPCvbLcIOKUT7gqRSXCaXr-HWoX4NcNaZ6blwVSMuIkb_A73uikh06icfTQ3u4rR7IXn8aYPz_CgfcxqpO-5pWUufeLjuXSquRSJ9j8CfqEaIak1ay3-X987gFfQf3d8zh4bPxoyForKGvPe8D3EihP3mkWvLL0Ndh71mQnN5IEL_X6mpb2a6-pS6J4NWQp5qYBckMRPn8sTZk_DV17BSIm1yYlNWnSha05F1CU0B34bNLrcDMG5_q4cbfNijBqzttpiLlIdNS_C4IyMk0c8oc=w828-h646-no?authuser=0"> 
              <br>6. click on code.<img src="https://lh3.googleusercontent.com/q-3CgYMP8o_7VDY8kKvUNOWr5aqpqRThBSEeII62hjdqEdhE8TsgEKHxjcJP9mV-FezQapf2bzq80lPg1DflFWqpxdbY__uT7PZSJEyggKo085YUUdIrv9DBOUo6b5N7SDXl_B2oxxfD98t3HVr17JZY5BXDUFs_yn5ZEfK6iniBxkJuWTZ51SNjpAybjBEWsMfi3WnDkfoQRVjoa7yNMkNqb0VeUXS_b9nYIoblST57bqBK5WXTpEJAEHv2289glyllsGaubfy8oktHpyDKp3dEOS8X-FVmsCS7o3meDEqZuOL1BbZo4SKYt7-5QpAL-J2GtT-rOvmj3RkO5pN1pouVsHEVWeSqqHPAs9Kr4a_Ryl6WCVXtCt1AzzYZneo5QgLstTeKRP5TIO6mtdHTbK2qyNXymQ-JvxoZaBHI61WlzMF5x0MYKo6GMYYoARZIlbeu0GwlXoFXqL6kDKcYK7bDfL2xYyIY5YXPpvLF3BZmku0LUOFc4KCM_xsBu8FXQw2v3UCjHMqAmVyPBSPqYjfBzBiz2ZHBTuYpCqcZiFxGBg7DPbkt31XsoUdE-81tsjnLVkq9aoHN2mCWo3M3vZh1qV--a9Pod_ZP_XGOd_kWXe0qew65Dm00RKe7LQZWBjpcMfjbuQvPNl_PBBFMOSHpFxQM4GE_vdcF6zTkd1Lwyi2F-ytXb88vExlM=w1054-h284-no?authuser=0">
              <br>7. Either you can choose from existing Enhancement 
              implementation or create new enhancement implementation -> provide implementation name, 
              description and save( either in local or your package ) -> select the implementation name<img src="https://lh3.googleusercontent.com/3kwUXrnGqIXbUB9xXY-iL7W6Tjm_ZYO77uqjbHQD2XH1YPTYkeE9tG-2NFrfLXL9az_kRK_QjVCJ0IKZ_jjS9FyKPhH40AN4UW07xejZVkO4GVzcjc5OlxucRb-nPBg4VS9InpIZYzbd2eyasqyTy4D2jbqWXotIwGCOSkW4fNUZjKjA5ETrBVJTJA9cQ6ORB6AleXiOQQjptruof_mb39MWLs3xi09dVwl45EJBuMY6cQkSe4VyQpJEqj_4GqOnmoNhD7yHysMcfMygcWaDuxiy6UXMvt67lLOzEg9iN2lBHNTlZ6t72wT0bb1y5Cu5Mo0EOc9_TJQTvfJ_AxZZqr53_qTRTjus93Nm4qjQYCJG-pc0Pp8heK24NvpH2kA8069BWhC7rilvs20r1dTp7vASuA_Gy65JCM8U2ARiFDzVBQAZXYOlyo6WAB6J_AVZ7UEua36Z6IoRpUSjLSFJRLcoRWdFwCFU8GL5asZWeMbC7wYHuk4PRjueFTTTpRK2cBVd-K2A0-rwqQ_Lscd8eYJESGd1zYJnfQWLEUt7O_8NKwQtu2wrlY2bMhSe7yNuM_RYpsuuW8mk-GGFFxDHTQ2jJ92gXsZM2auqdFlNdU9pSbuYFWSF8mUE9pZilMgcnlwfrLEOeTA5SEPHIpCufEsSpPmv6YIhCvbP5D4NV9zvw1C2b0OjH46Jf_0L=w1440-h216-no?authuser=0"> 
              <br>8. Provide the logic.<img src="https://lh3.googleusercontent.com/DcuNUy5YPLwxzF8j4EXP7hv0_AU6l0C8NroFx_n_ofZK9x81ptTYfCn-Fxc_tQ4jnrGmA11XZNPcy-HTqYnxxo8_GtMyn_BhEA4LBPE9ybDAA3gqKiScF9-5543TwLehmqNYqpY6KHItHHMiMWMlKrdYv2Ws3gY9n8zV3kRW80ivQXx2hTZqeRs0ziqNQYMbHWBbhGHNmmmSdUuRwfbJK_GwObL1uZVyq73ZUIw98u6W0XCU9xjBIfZSC11yIo7F9wkkkU0RQpmi6Cqqzd3iQwTmIJBmkw9a1Ruvj9_Rj8cFEeVEiSwjLr3791BmQTyDRG8DvY3d3JvdaT1oMr8VDP5ZfJIEiAJ2WUqQi1xZb59Kj7idqBTLuQJjyR623fH4n1fQWgztsAViONarPLLpZ0-no0GsU_7zCKC64aRnTbXogHBeu9bo0hFJ2PtiePwh_WQr1f4Z0q6rMtmeOY11Ov8av4gOet-w5rURwViGT5jUhiMyHIRZnGMGdbMM_a3d5yOrAwiHiae0hgRZRuIJw_5_P_06ED5kCWIS8KuuLfcf-1zA78qjw3GAYLu9ZWaW-RpJn3K40SGKCmQiUSDDwictZdKXwGfwgxqWxi4KZWyV9dvxxLNIfqfCMjr85S8eZh-8KKI5a6XYMs_sUP2_iq7UJeSTR_zDTtnxmp-DXrM37zwiroMPE0x55YM8=w988-h158-no?authuser=0">

              And your done with your first User Exit Imlementation. &#128522;
          </p></li>
        </ul>
     </li>
    </ul> 
  </li>
<!-- Customer exit -->
  <li><span class="caret" style="color:blue">Customer Exit</span>
    <ul class="nested">
      <p>Customer exits are also same as user exit in terms of functionality. It acts as a hook to the standard program where you can hang your own add-on functionality. Customer Exits refers to all modules like SD, MM, FICO, PP etc. whereas User Exit is generally refers to the SD module. 
There are three types of Customer Exit.</p><a href="/function-module-exit">1. Function Module Exit.</a>
      <br><a href="/menu-exit">2. Menu Exit.</a>
    <br><a href="/screen-exit">3. Screen Exit.</a>
    </ul> 
  </li>
<!-- BADI -->
  <li><span class="caret" style="color:blue">BADI</span>
    <ul class="nested">
      <p>Business Add Ins aka BADI is similar to the Customer Exit. Acts as a hook to the standard program but the approach here would be <code class="highlighter-rouge">Object Oriented</code>. Also BADI's can be implemented multiple times. 
      <br> Each BADI contains <code class="highlighter-rouge">one Adapter class</code> and<code class="highlighter-rouge"> one Interface</code>, Adapter class will implement the interface and thus provides the interface for customer implementation. If the BADIs has to be executed under certain condition, then the Adapter class ensures that only certain implementation is executed. Basically to use BADI you'll have to create the instance of the adapter class in the application program and calls the corresponding method( defined in the interface) at the appropriate time(Explained in detail in BADI Implementation &#128512;).
      <br><a id="types">Types of BADI</a> :
      <br>1. <code class="highlighter-rouge">Single implementation BADI </code>: A BADI which has only one implementation (single class) is called single implementation BADI.
      <br>2. <code class="highlighter-rouge">Multiple implementation BADI </code>: A BADI which has multiple implementations is called multiple implementation BADI. By default all the implementations will be executed.
      <br>3. <code class="highlighter-rouge">Filter BADI </code>: It is type of BADI which has a filter value so that only those implementations which satisfy the filter value are executed. The remaining implementations are not executed this type of BADI is called a filter BADI.
      For more detail on BADI definition and implementation check below links :</p><a href="/badi-definition">1. BADI Definition.</a>
      <br><a href="/badi-implementation">2. BADI Implementation.</a>
    </ul> 
  </li>
<!-- Enhancement framework -->
  <li><span class="caret" style="color:blue">Enhancement Framework</span>
    <ul class="nested">
      <p>Enhancement Framework in SAP ABAP is the new enhancement concept that helps in enhancing the standard code. They provide more flexibility compared all of its predecessors( User Exits, Customer Exits and BADIs). 
      Few of its advantages are :
      <br>1. Easy Maintainance.
      <br>2. SAP can deliver more than one business processes in the same code.
      <br>3. Customer can activate the business processes.
      <br>Since SAP release 7.0 the BADI have been included in <code class="highlighter-rouge">SAP Enhancement Framework</code> but the concepts are same &#128512;.
      <br>Types of Enhancement Framework:
      </p>
      <li><span class="caret" style="color:teal">Implicit Enhancements</span>
        <ul class="nested">
          <p>An Implicit Enhancement is a source code plug-in point provided in SAP objects. Unlike Explicit Enhancement, these enhancements are almost present in each SAP objects and mostly at the begining and end of the source code of a program, Function Module, Method, Subroutines, even at the end of Structures, at end of Include Programs etc.
          <br>How to find Implicit Enhancements and implement it is explained in next blog<a href="/implicit-enhancement"> Click here.</a></p>
        </ul>
      </li>
     <li><span class="caret" style="color:teal">Explicit Enhancements</span>
        <ul class="nested">
          <li><span class="caret"><code class="highlighter-rouge">Enhancement Point</code></span>
            <ul class="nested"></ul>
          </li>
          <li><span class="caret"><code class="highlighter-rouge">Enhancement Section</code></span>
            <ul class="nested"></ul>
          </li>
          <li><span class="caret"><code class="highlighter-rouge">BADIs</code></span>
            <ul class="nested">
              <p> I have already explained the BADI concepts above in this blog.&#128514;</p>
            </ul>
          </li>          
        </ul>
     </li>
    </ul> 
  </li>
</ul>