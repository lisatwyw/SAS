

## Resources

- [SAS to Python Kaggle](https://www.kaggle.com/code/faizulislam19095/sas-tutorial-a-guide-to-start-learning-sas)

- [Refresher on Tabulate](https://documentation.sas.com/doc/en/pgmsascdc/9.4_3.5/basess/p0ergzq2qw19inn1vzztc40gpmh5.htm)
  ```
  options linesize=84 pageno=1 nodate;
 
  proc tabulate data=year_sales format=comma10.;
     title1 'TruBlend Coffee Makers, Inc.';
     title2 'Number of Sales by Each Sales Representative';
     class SalesRep;1
     table SalesRep;2
  run;
  ```
  
- From [SAS Proceedings paper#3117 in 2019](https://support.sas.com/resources/papers/proceedings19/3117-2019.pdf)
  ```
  data claims_flag;
     set claims_orig;
     label af_flag = "Atrial fibrillation diagnosis code"
     tia_flag = "Transient ischemic attack diagnosis code"
     pe_flag = "Pulmonary Embolism"
     ;
     /*----------------------------------*/
     /* Initialize flag variables to 0
     /*----------------------------------*/
     af_flag = 0;
     tia_flag = 0;
     pe_flag = 0;
     array diagvar $ dx1-dx4;
     
     do over diagvar;
     if dx_version = 9 then do;
     if diagvar in: (&af9) then af_flag = 1;
     if diagvar in: (&tia9) then tia_flag = 1;
     if diagvar in: (&pe9) then pe_flag = 1;
     end;
     else if dx_version = 10 then do;
     if diagvar in: (&af10) then af_flag = 1;
     if diagvar in: (&tia10) then tia_flag = 1;
     if diagvar in: (&pe10) then pe_flag = 1; 
     end;
     end;
  run;
  ```


## Possible Tasks:
- Article on [BCC19C](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC10914982/)
