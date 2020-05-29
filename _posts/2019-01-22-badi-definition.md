---
layout: post
title:  "BADI Definition and Implementation"
author: sal
categories: [ BADI, Enhancement ]
image: assets/images/badi-definition.jpeg
tags: featured
date: 2020-05-21
---
Before starting this let me tell you one thing you'll rarely create BADI Definition in real time scenario. Generally you'll use existing BADIs or Standard BADIs,<a href="/badi-implementation#here"> How to find it?</a> <br><b>SE18</b> is the T-code for BADI Definition. But before creating BADI you'll need a container for it i.e an **Enhancement spot.** This is the container in which you'll develope your BADI. If you are thinking **WHY?** its because using **Enhancement spot** you can add your code in the standard code without needing the access key, which implies standard code won't be disturbed. 

`Use case:` Let's create a BADI Definition to get tax value.

## How to create an Enhancement spot?
1. Go to object navigator( SE80 ), navigate to the package in which you want to create the enhancement spot, here I'm creating it in local($tmp) package.
2. In the context menu of the package choose <br>Enhancement->Create->Enhancement spot.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3ceRArtylstLvgzBtOakGlt7Ul3GqvGKwHxfRaIb6czAVANAIAmYCGsFm5FUHkgDJokl3tNORz3qDMdTQ0tY4Ok1dJN8mrAO48GNwXvU1cw7Bw-wuobRpUk2oCByUALVS61fMbwyrRRPUNh0Bu9I6iv=w665-h788-no?authuser=0">
3. Enter the name and description and save it in your package. It will look like below screenshot.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eyIWlVl-fxywpAefFjGas6a1Z5QMe7vwHPkma9Z0jD1Kks5ImGBLE3n3ROsnH4Le_w5U7tpUDqihGwxxzLJ3AAHzMlve4sBeKjf2DPZ1xGfEXUS7NyI9D2kMemfvlaVwBnu36sZFtDz9mKyfzu-di7=w1440-h457-no?authuser=0">

`Another Way:` you can create the enhancement spot in the SE18 T-code itself.

<img src="https://lh3.googleusercontent.com/pw/ACtC-3exatHMK9IbZvlMPwm9PIxFAt33v-b8O5N6ObTBr8mlhY1Nuflj-4M4C5jwy4wM_WOP0tcYLaL-HBU3cExRuwtbcCMh-4RAmxJFJ9VU7p7vu792C-C3ppmV9sI0RVtlAt3k8a2rR3IV7KM-56XpQ3Sk=w852-h380-no?authuser=0">

## How to create a BADI Definition?
1. Within the same Enhancement spot, choose the create badi pushbutton on the left.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3fzC7x4mMTm_oyWnI_NwPe903pklt-u0QSM3AFgj03VqxKdC4LSHqlTTc1M3e9wO0ConXN3YbLX43j3mxwq9Nk6QolPDvfz4KENrqD5T6X4uHDzDCnuszOK6nyU7-DUuK6XRqn_IxS35MRdIesQAoBp=w1320-h364-no?authuser=0">
2. Give name starting with 'Z' and short description of the BADI.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cbwnfnATcGCKMIjTm07G32JAX-0Kr0QgnluWk8KaaOeNNmkDj_-dQgXUJZ4AbPK7DAkiga1tiSUInofbz4UMSSXogI8EkyK4ouFgKxVh5wmSlUAOpdMBmgQmud1RMKUVDyYjfi7MufuyuGYJXKI3Dx=w1062-h228-no?authuser=0">
3. Choose the type of the BADI from the checkbox in Usability section. 

##### So the BADI creation is done? NO, you still need an interface where you'll define your method and while implementating the BADI actually you'll implement this method and write your logic.

4. Expand your BADI name and you will see the 'interface' icon.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cudD2HzHlvrKllY6AmyWgnz0vsMErKC1JDzNkAa91xR3QNn7GNlT3wAoD7cp5ifkCAcvJ-OSbvRr1NOXL0yDbCFwgvw08rQ_0uVcYivxkH8jAg6jbZTLpVkpuGQwiFXPfvwuUiF_Fuh0_x1D1B2LwO=w508-h470-no?authuser=0">
5. Double click on it and provide an interface name either existing or a new one, then click on change pushbutton, if its new one it will ask to create first.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3dUd_qwd2IUSbkJbsJ752Au9Hi_ugzFrgOsGX1N7Ae1CBpmqrAcmL3MTIHEPnKiEY0vtBplzKa3ofkvFRRc2B5iGnhoAraalxivspfVHagtMrkqI6_V7ORzDGP0PQfnHL-BeuCWHHdTkPLh7VCUli4j=w1114-h600-no?authuser=0">
6. After clicking on change pushbutton it will take you to the class builder where you can create the method you need for your BADI. Simply now provide the method name and parameters for the method.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3enidKW5qXvbbv8yV3CZ__emQvJDHxF7tF8vPxAtCcxhy0R6Fj_xk2_nZkZiaKZK_HgPlZjFadr2rZ0_1piHGc-F3xDb2WKd1qR5fzsDKsa-12G7-gS7GpIkILu5D33ZQ6j06_fk69-MmI2O3h3G1vt=w1408-h302-no?authuser=0">
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cz6DIva2sYq7PdipzDg_TgGBNsAWFqr7CivazOjqEVObnQXhwejRg2QExGiVXdHgUh5uXwC6KtYVq1U9VFZfo6niZ9COwGna3Kn0IKYWxEMYbvwWCsCGKMvp0JII3hoBRKHx-SP43ROyITNyCsDAmJ=w1296-h404-no?authuser=0">
7. Save and activate your BADI as well as Enhancement spot.

This is a custom BADI you have created just now, and you have to implement it that I will show you here but in real time mostly you will implement Standard BAPI. To know about implementing standard BADI <a href="/badi-implementation">Click here.</a>
If you will run your report program where you have used this BADI, it will go for dump hence you have to create an implementation for the BADI.<a href="#here" id="back">Try executing your report without implementing your BADI.</a>

8. Go back to the main screen and right click on Implementation -> create BADI Implementation.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3e-bHuAgv_acTJ3_lhM05LO3Tm14vQrbijm0Jzi_XiMLCgM4dEZUB-N0Vw03nZFwgC1XRl4DM0j3-MWES2ov88UGWWPJsh3XvfFJBYFqTt3jWfgezrW_l106Kwx7qyaSL5NBeEXkqyqjVXOFWaTnJZy=w1440-h447-no?authuser=0">
9. Provide Implementation name and short text and click on continue.
<img src="https://lh3.googleusercontent.com/lzwLHiLZoYq0f9OwzeQonyNrh0uVMvNnyIXJsxU1W7uHm6c4ADFpT1zcTS6drJwyYe-tt9KigPXeGTbmpB2ja-JMMwnOXD33PhqIKGPiqemnwK7kBxT405Lbye7HQ9NHThHSsYk00eRb3cYOFzP1W7E-Terlq04AW5oNlFE2Noy6F-Bo2teU83YrN-Yx-ilUljPjwXduo4vvkffhs6A5HnU_nrhpd-4hl3diA3BDcBTF83P2g8GoMMK8zz_nSscdJzoxTYJPbre1m2uOnqBQkxGn9KN1NLQmUJA-UqVMrfSJ9EVJQi48OxONptRs9JnIsps6c6v_PaDX7D4oFnRIWuYdGtufaK5h2MQgt-K9HpB3q6gTG8HZk5aTrc3C8TeHshkw9RtyZnIbON7158x_1ea3NRkqFSbfj3DiHkSV1vcpUUWDlCurwXL6Lp4C-P_hzJtL5cCrab68z6-GpyJh4xTU6IBJfNbiAfNj69530cSVlCqCKD7A0O4q9Ixlb_W6ZMQF62dR_AcCkVtKgqR4IanfgSVO6fPg4T37e-BeqZFJI1KsOcEnWrt2E9Bzr9bADQYCy2juS3uDIM_jbZ_rONgOWixo8kEdgVja69pDcbFL8ZjqKKZS5IEBh-_utpfh1KGXPE21ZC4ZprQGlNx0iCETKjdFGu18EcjeXDiWgSOkOJ_xcV9wEWflVcaq=w1440-h259-no?authuser=0">
10. Click on continue and provide the implementation name that you just created, give description and then give a class name which will implement the BADI.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3ep-u2AdVub_lrnUr7pcQLrRECpE11RMFV1P2A-gpExsawfTV33M14Vgcb_dug3pY16kHW_PikyB-jGZE-NHUSCY4rCyTwmW1Ol_xO8xys6e1doR17Jnx4auDiPGAryg2Spp8VnPCQHZ1d79BM6dgOr=w1440-h259-no?authuser=0">
11. Now in implementation section you'll find your BADI Implementation, double click on it.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3fYf8wgcWB5pZDIID1xrLeH2P_bTk6szAbnD3jLzVB3kmy3Cll3Hnqw2-ibx9Ap6E0j8INIV2OrnamPvSsjEFiqpqf_ccT9R9BCP8oOJjJSq5vRlkFUaOkw9psYxam1Rki_WEkxQCajPIeqE1R6YEir=w1440-h775-no?authuser=0">
12. Double click on Implementing class and you'll see the method <code class="highlighter-rouge">Z_IF_CALC_VAT~GET_TAX</code>, double click on it and write the logic.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3e4OM0qqqjpM0idq9SrBE9ajzyx9j24B8rRA72Vtiu0YvgITFpJCgfiC1QvOD1UurcE5gdQEFdEzY1JrHr8nEf7bvW7R2MGMX1yHoeh9dJ5e8qYqMfsLOTFZ5pXxj6O3dQbUamVuj6ZTPS_ez1ira2v=w1440-h380-no?authuser=0">

{% highlight ruby %}
 DATA percent TYPE p VALUE 20.
 ex_amount_tax = im_amount * percent / 100.
 ex_percent_tax = percent.
{% endhighlight %}

## <code class="highlighter-rouge"><a id ="here">What's Fallback Class?</a></code>
- If you run the below ABAP Program without implementing your BADI, you'll get dump. Why? because you have not implemeted the BADI yet. 
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eZMVNwQKbu-HWMGjDT6NQaE6yyzrtpUXe1zpl666FcRcwmn4L26EKtjavQzCsXpY71UjTDgeJpkFBoAD9d_CLcOXJgW0v5vX0eoVrtm2hRRVH38c9S_4l-JrL4my9uy3gQb0xQ7gluIjPpbQOWjhvu=w1038-h754-no?authuser=0">

You can handle this error by catching the exception `CX_BADI_NOT_IMPLEMENTED.`

<img src="https://lh3.googleusercontent.com/pw/ACtC-3cYdavhQuX3o7yXejAjrrPTADw65IEeVxIqtbQgg1U-N9XhPsXUg2lYR2XbL80r1nVV5v_NaIvSRn86ia8w-5U9t_bCdNEousLmZ4EgNWrN7pr7siAqMg8Wnc-OAyVGL_CQjwzUF67UNp7l8BkryluQ=w975-h788-no?authuser=0">
- A better solution is to use Fallback class. A fallback class is used when there is no active BADI implementation. The `GET BADI ` command return a handle to an instance of the fallback class and the respective `CALL BADI` calls the methods of the fallback class instance. As soon as there is active BADI implementation, the fallback class is no longer used at runtime.

1. Select checkbox `call fallback class if no implementation is executed` and enter a name for the class.
<img src="https://lh3.googleusercontent.com/pw/ACtC-3eH7HlgqoixAZ2usFFjGD3m0APwX63YihrUKr-VtxuBQ9mRLEM7crV9f98s-zy9GLnwb60ShsGG9H9nNbhTlrgU3Hp0rkQkkui4fzqh0ppkAGis6g97ofyqk5Yc7Zlm9l_R14XrAppNx--cZ2x5IPmw=w999-h788-no?authuser=0">
2. Choose change button to go to class builder. 
<img src="https://lh3.googleusercontent.com/pw/ACtC-3cLQNri4Ziu6uE4C9UE9hRLS37pNLQMeBzrS3yn1g4QKvrt5RCqf5yMwotQviKOVIK1oH4JNyKAR0u7301r81eJTaam7b7qaG8qXET37gQVkjCr_j-a3X44iv06_hB4aYk9Hjme2lTf0M2iLIZkKOXQ=w1236-h322-no?authuser=0">
Here you will find the already created method, just implement the fallback logic into the method. 

<a href="#back">Go Back to create implementation for BADI.</a>