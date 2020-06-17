---
layout: post
title:  "Create your First CDS View using Eclipse ADT"
author: jane
categories: [ Jekyll, tutorial ]
image: assets/images/create-cds.jpeg
tags: [featured]
date: 2020-06-24
---
An ADT-based surce code editor( Eclipse, HANA studio etc. ) will help you to create DDL sources. On activation, the CDS entities defined in such DDL source becomes a part of ABAP dictionary objects.

Once you have configured `ABAP Development Tools(ADT)` in your Eclispe, go to ABAP perspective and add your project. You can see your project in the `Project Explorer`  expand it and you will find all the package in your project. For demo purposes let's create CDS entities in the `$tmp` package.

There are few types of CDS Views : Let's explore each one by one &#128522;

## `BASIC CDS View`
Basic CDS view are basically used to fetch records from one table, also you can say it is projection view.

1. Right click on package name -> New -> Other ABAP Repository Object.
2. Type 'core' in search box and choose Data Definition. Click Next.
![cds](https://lh3.googleusercontent.com/pw/ACtC-3c1I_vx9TCrQ0r0Ht7WXBYViTm-A4Coq9FCS_9SKFlyXQlEaEX2F3acydFfT2HVNZyUIshDe_FYkGErHgczGJy8Z0DmVdp6yI1K_hhddj64-Gq9ISSviQ8fH_X8cOXmIleMPO2XQCq5DjAORykN6DVu=w1009-h788-no?authuser=0)
3. Give CDS view name and description. Click Next.
![cdsname](https://lh3.googleusercontent.com/pw/ACtC-3d52BKCmzp3KUA_SgqFAAj407ZpjcUrceOzkT7JpgyOm-WD9TSu9m39oj9w1boeg3JUeYg9xkB66cN8fh-bGYQbdUQqTAvHlK401pmhTUlybo1Pe7AbynzF3yuCrOqvyQz8NRKrjFDLLYG4j1_2ZDTO=w977-h788-no?authuser=0)
4. Provide Transport request if any. Click Next.
![tr](https://lh3.googleusercontent.com/pw/ACtC-3fvzPg473R2VuffwhT3nIGxNBSHgI9svqKcxGtCFo1ahKQmCWZw-Meedt1WmdqE3cKyaQVUDI0aSYR8ICvsdJvI9m-75VskKog_gXpaClYw6rRvW861dyYXsNGdjMcjM-RVfNwuwUt63zQEMAxzW9Jm=w969-h788-no?authuser=0)
5. Chhose `Define View` option and click on finish. The other types of CDS views has been discussed further in this blog.
![basicview](https://lh3.googleusercontent.com/pw/ACtC-3d4jKnlYawKASE7Wu8sJbew3xg3KGIuyi2uRPl43Z-lCTnCtmGtnE5EW_NciHBknWC9H666-VCYLHex018Aj57fSvJ0eQG8-OYENB2l-1fCUui4YbA1HutOe9_XbROdVqYJeEXGssmAMy6eykWeCcCo=w968-h788-no?authuser=0)
6. You will get the template and fill the required data. Give `sql_view_name` diffrent from the CDS entity name and the length must be less than equal to 16 characters. Here CDS Entity name is `ZBASIC_CDS` and sql View name is `ZSQL_BASICVIEW`.
![cdsview](https://lh3.googleusercontent.com/pw/ACtC-3cvDEAFjUYB54MeRoyO9FACj9riAYSKaA7v9RmLQeApLODybWc7dYnJhGnKhk7T_Iq8CK1xlxD8Sq_vImp4Wxmhi2l7Jc8ix1CwlqMu2uIeaq9pYRaoW1O5FPc60y8UMcs6NmzB1VKKJvgia_H-1Rdz=w988-h432-no?authuser=0)

You can always change the template of you CDS view. Go to `Templates` tab in the tabstrip below the edito window. Then select the whole code(Make sure you are in edit mode, to go in edit mode just type something in the editor it will automaticaly go to the edit mode) and choose another template and double click on it.
![templateselection](https://lh3.googleusercontent.com/pw/ACtC-3eZwP6mY9_BM_fvuZRjZQOvnuJTE_nY_-6ksJxpzbKetqHoCJTYYDvaAxH3k__wmC-jCL_vLYudLiH6_4tcFE7gkWXz9gvndVRUs1t9MV0V2vxWsog0YowUuajOL0KhbAQfpRvtHss64ilfDRHla6xu=w885-h788-no?authuser=0)

Once you activate your CDS entity, two objects are created: `SQL view` and `CDS view`. 
Let's search in the SAP GUI the view you created just now.
![abapview](https://lh3.googleusercontent.com/pw/ACtC-3cnoDUdj5WYQyQ3zXZNNwrm4TjE6dqS9ZkPg_CeY7VNvh1fjlXk3Wa9hNYXw7rMhGkuYDb2uupQmpYFLqDpqcMAoD05zuc-D9C7zFN4J5MuuqN4hvTJbvz2nZVIcNphD3uBwfnxmm1nxp8wlSkRzCQU=w868-h748-no?authuser=0)
![abapview](https://lh3.googleusercontent.com/pw/ACtC-3f1ExM2965EkuWtMRKZxbBmTK4d6pMm13CpmYRcqqmAhBYSxhemTqQSI8r-ttw8FxDJJut4IXLhdEL-3FK9DpM-a99AwY7l5UlULczbi4ORuDUrTmFCqXOvOFcT0REe2o6EZ7GiX54m9MVBSKkBY_4V=w1440-h523-no?authuser=0)

The SQL view is visible in ABAP dictionary but can't be edited there. It represents real database object, is an ABAP data type(structure with client field) whereas CDS view carries more semantics than its SQL view. It is not created on the Database and it is not visible in the ABAP Dictionary, it is also an ABP data type but without client field. You can add additional semantics( Annotations ) in CDS view but not in SQL view.

There are two types of annotations