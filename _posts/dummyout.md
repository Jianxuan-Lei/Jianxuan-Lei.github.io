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

	eststo: estpost sum i.x
	
An obvious solution is to create dummy variables in the first place before you summarize them. Stata's system command can help you do this:

	tab x, gen(x_)
	
However, this becomes cumbersome when you have multiple categorical variables, since you probably need to write a loop:

	foreach var of x y z {
		tab(`i'), gen(`i'_)
	}
	
Moreover, the generated dummy variables do not have neat tables that you can use later to esttab your summary statistics. For example,

	sysuse auto, clear
	tab(foreign), gen(foreign_)
	describe foreign_*
	
	
		      storage   display    value
	variable name   type    format     label      variable label
	---------------------------------------------------------------------------
	foreign_1       byte    %8.0g                 foreign==Domestic
	foreign_2       byte    %8.0g                 foreign==Foreign


The "dummyout" Command
------
This "dummyout" command improves Stata's "tab(), gen()" command in the following ways:
	* Dummyout accepts multiple variables and does not require a loop
	* Dummyout uses value label numbers to label generated dummy variables, instead of using sequences
