# utl_explanation_of_pdv_with_two_set_statements_and_three_input_tables
SAS Explanation of pdv with two set statements and three input tables

    ```  SAS Explanation of pdv with two set statements and three input tables                                                                                        ```
    ```                                                                                                                                                               ```
    ```     ALGORITHM                                                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```         data want;                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```            set class(in=a)                                                                                                                                    ```
    ```                class(in=b);   ** this is one dataset with 39 obs;                                                                                             ```
    ```            output;                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```            set class(in=c);                                                                                                                                   ```
    ```            output;                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```         run;quit;                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```           There were 3 observations read from the data set WORK.CLASS.                                                                                        ```
    ```                                                                                                                                                               ```
    ```      WHY? There were 1 observations read from the data set WORK.CLASS.  WHY??                                                                                 ```
    ```                                                                                                                                                               ```
    ```           There were 3 observations read from the data set WORK.CLASS.                                                                                        ```
    ```                                                                                                                                                               ```
    ```           The data set WORK.WANT has 7 observations and 1 variables.                                                                                          ```
    ```                                                                                                                                                               ```
    ```      EXPLANATION                                                                                                                                              ```
    ```      WPS/SAS (same result)                                                                                                                                    ```
    ```      =====================                                                                                                                                    ```
    ```         data want;                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```            set class(in=a)                                                                                                                                    ```
    ```                class(in=b);   ** this is one dataset with 39 obs;                                                                                             ```
    ```            output;                                                                                                                                            ```
    ```                                                                                                                                                               ```
    ```            put name= @22 a=;                                                                                                                                  ```
    ```            put name= @22 b=;                                                                                                                                  ```
    ```                                                                                                                                                               ```
    ```            set class(in=c);                                                                                                                                   ```
    ```                                                                                                                                                               ```
    ```            output;                                                                                                                                            ```
    ```            put name= @22 c= //;                                                                                                                               ```
    ```         run;quit;                                                                                                                                             ```
    ```                                                                                                                                                               ```
    ```         NAME=Alfred    A=1   read ob 1 of the 39 in (a+b)          > output    1                                                                              ```
    ```         NAME=Alfred    B=0   not there yet (only after 19 from a )                                                                                            ```
    ```         NAME=Alfred    C=1   read one                              > output    2                                                                              ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```         NAME=Alice     A=1   read ob 2 of the 39 in (a+b)            output    3                                                                              ```
    ```         NAME=Alice     B=0   not there yet (only after 19 from a )                                                                                            ```
    ```         NAME=Alice     C=1   read one                              > output    4                                                                              ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```         NAME=Barbara   A=1   read ob 3 of the 39 in (a+b)          > output    5                                                                              ```
    ```         NAME=Barbara   B=0   not there yet (only after 19 from a )                                                                                            ```
    ```         NAME=Barbara   C=1   read one                              > output    6                                                                              ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```         NAME=Alfred    A=0   read ob 4 of the 39 in (a+b)                                                                                                     ```
    ```         NAME=Alfred    B=1   ** no more obs in a get one from b      output    7 (out of obs in B so stop;                                                    ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```         Up to 40 obs from wantwps total obs=7                                                                                                                 ```
    ```                                                                                                                                                               ```
    ```         Obs     NAME                                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```          1     Alfred                                                                                                                                         ```
    ```          2     Alfred                                                                                                                                         ```
    ```                                                                                                                                                               ```
    ```          3     Alice                                                                                                                                          ```
    ```          4     Alice                                                                                                                                          ```
    ```                                                                                                                                                               ```
    ```          5     Barbara                                                                                                                                        ```
    ```          6     Barbara                                                                                                                                        ```
    ```                                                                                                                                                               ```
    ```          7     Alfred   (read the 19 on a then one ob from b and emd of data)                                                                                 ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```
    ```                                                                                                                                                               ```

