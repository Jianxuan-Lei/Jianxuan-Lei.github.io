---
title: 'Dummy out Categorical Variables in Stata'
date: 2022-10-19
permalink: /posts/2022/19/dummyout/
tags:
  - Stata
  - Resources
  - category2
---

Summary Statistics for Categorical Variables in Stata
------
It is somewhat painful to produce a table of summary statistics for categorical variables in Stata. The issue is that the popular user-written package esttab does not accept factor notations for summary statistics. In other words, you cannot simply get neat tables with the following command:

	> eststo: estpost summ i.some_categorical_variable

The "dummyout" Command
------
This "dummyout" command improves Stata's "tab(), gen()" command in the following ways:
	* Dummyout accepts multiple variables and does not require a loop
	* Dummyout uses value label numbers to label generated dummy variables, instead of using sequences
