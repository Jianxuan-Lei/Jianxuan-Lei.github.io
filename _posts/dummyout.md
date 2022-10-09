---
title: 'Dummy out Categorical Variables in Stata'
date: 2022-10-19
permalink: /posts/2022/19/dummyout/
tags:
  - Stata
  - Resources
  - Tables
---

Summary Statistics for Categorical Variables in Stata
------
It is somewhat painful to produce a table of summary statistics for categorical variables in Stata. The issue is that the popular user-written package [estout/esttab](http://repec.sowi.unibe.ch/stata/estout/) does not accept factor notations for summary statistics. In other words, you won't get neat tables by simply typing the following in Stata:

	eststo: estpost summ i.x
	
One potential solution is to create dummy variables in the first place using Stata's system command:

	tab x, gen(x_)
	
This is cumbersome, becase a loop may be required when you have multiple categorically variables:

	foreach var of x y z {
	    tab(`i'), gen(`i'_)
	}

The "dummyout" Command
------
This "dummyout" command improves Stata's "tab(), gen()" command in the following ways:
	* Dummyout accepts multiple variables and does not require a loop
	* Dummyout uses value label numbers to label generated dummy variables, instead of using sequences
