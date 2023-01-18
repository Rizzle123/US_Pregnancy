# US Pregnancy

This project is an academic piece that examined factors that influence total number of children among women. The data set used was retrieved from the GSS website at https://gss.norc.org/get-the-data/spss in the year 2015 under the heading **Individual Year Data Sets (cross-section only)**. Therefore, all credit is given to the GSS team. 

All analyses were done using SPSS on the GSS 2010 data set. 



The codes for the study can be seen below and copy was made available in my report :

1.	FREQUENCIES VARIABLES=sex
           /ORDER=ANALYSIS.
2.	FREQUENCIES VARIABLES=wrkstat marital padeg madeg race
  /ORDER=ANALYSIS.
3.	USE ALL.
COMPUTE filter_$=(sex = 2 & age <= 49).
VARIABLE LABELS filter_$ 'sex = 2 & age <= 49 (FILTER)'.
VALUE LABELS filter_$ 0 'Not Selected' 1 'Selected'.
FORMATS filter_$ (f1.0).
FILTER BY filter_$.
EXECUTE.
4.	FREQUENCIES VARIABLES=agekdbrn age educ Recode_child_ratio
 	 /ORDER=ANALYSIS.
5.	REGRESSION
  /MISSING LISTWISE
  /STATISTICS COEFF OUTS R ANOVA
  /CRITERIA=PIN(.05) POUT(.10)
  /NOORIGIN 
  /DEPENDENT Recode_child_ratio
  /METHOD=ENTER age.
6.	REGRESSION
  	/MISSING LISTWISE
  	/STATISTICS COEFF OUTS R ANOVA
 	 /CRITERIA=PIN(.05) POUT(.10)
  	/NOORIGIN 
  	/DEPENDENT Recode_child_ratio
 	 /METHOD=ENTER age agekdbrn educ.
