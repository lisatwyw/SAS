
From [SAS Proceedings paper#3117 in 2019](https://support.sas.com/resources/papers/proceedings19/3117-2019.pdf)
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
