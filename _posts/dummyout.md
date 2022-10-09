---
title: 'Dummy out Categorical Variables in Stata'
date: 2022-10-19
permalink: /posts/2022/19/dummyout/
tags:
  - Stata
  - Resources
  - category2
---

Easy Summary Statistics for Categorical Variables in Stata
======
It is somewhat painful to produce a table for summary statistics in Stata when you have a lot of categorical variables. The

The ``dummyout'' Command
------
This "dummyout" command improves Stata's "tab(), gen()" command in the following ways:
	* Dummyout accepts multiple variables and does not require a loop
	* Dummyout uses value label numbers to label generated dummy variables, instead of using sequences
