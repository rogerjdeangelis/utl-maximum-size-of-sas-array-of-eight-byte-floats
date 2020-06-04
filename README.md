# utl-maximum-size-of-sas-array-of-eight-byte-floats
Maximum size of sas array of eight byte floats
    Maximum size of sas array of eight byte floats                                                                                      
                                                                                                                                        
    github                                                                                                                              
    https://tinyurl.com/y8x5r9ey                                                                                                        
    https://github.com/rogerjdeangelis/utl-maximum-size-of-sas-array-of-eight-byte-floats                                               
                                                                                                                                        
    *_                   _                                                                                                              
    (_)_ __  _ __  _   _| |_                                                                                                            
    | | '_ \| '_ \| | | | __|                                                                                                           
    | | | | | |_) | |_| | |_                                                                                                            
    |_|_| |_| .__/ \__,_|\__|                                                                                                           
            |_|                                                                                                                         
    ;                                                                                                                                   
                                                                                                                                        
    SAS Workstation SAS9.4M6 64bit and Win10 64bit                                                                                      
                                                                                                                                        
    I have 128gb ram                                                                                                                    
                                                                                                                                        
    MEMMAXSZ    = 128,849,018,880 Specifies the maximum amount of memory to allocate for using memory-based libraries.                  
    MEMSIZ      = 128,849,018,880 Specifies the limit on the amount of virtual memory that can be used during a SAS session.            
    REALMEMSIZE = 128,849,018,880 Specifies the amount of real memory SAS can expect to allocate.                                       
                                                                                                                                        
    Temporary ARRAY                                                                                                                     
                                                                                                                                        
    array gb2[268435455] 8. _temporary_;                                                                                                
    array gb2[268435456] 8. _temporary_; ** FAILS ***                                                                                   
                                                                                                                                        
    *                                                                                                                                   
      __ _ _ __  _____      _____ _ __                                                                                                  
     / _` | '_ \/ __\ \ /\ / / _ \ '__|                                                                                                 
    | (_| | | | \__ \\ V  V /  __/ |                                                                                                    
     \__,_|_| |_|___/ \_/\_/ \___|_|                                                                                                    
                                                                                                                                        
    ;                                                                                                                                   
                                                                                                                                        
     2**28-1                                                                                                                            
                                                                                                                                        
     268,435,455    (temporay array max number of 8 byte floats)                                                                        
                                                                                                                                        
     2,147,483,640  ( size is 2gb)                                                                                                      
                                                                                                                                        
    *                                                                                                                                   
     _ __  _ __ ___   ___ ___  ___ ___                                                                                                  
    | '_ \| '__/ _ \ / __/ _ \/ __/ __|                                                                                                 
    | |_) | | | (_) | (_|  __/\__ \__ \                                                                                                 
    | .__/|_|  \___/ \___\___||___/___/                                                                                                 
    |_|                                                                                                                                 
    ;                                                                                                                                   
                                                                                                                                        
    %macro tst;                                                                                                                         
                                                                                                                                        
      %do i=268435455 %to 268435456 %by 1;                                                                                              
                                                                                                                                        
        data _null_;                                                                                                                    
                                                                                                                                        
          array gb2[&i] 8. _temporary_;                                                                                                 
                                                                                                                                        
          put "&i";                                                                                                                     
                                                                                                                                        
        run;quit;                                                                                                                       
                                                                                                                                        
    %end;                                                                                                                               
    run;quit;                                                                                                                           
                                                                                                                                        
    %mend tst;                                                                                                                          
                                                                                                                                        
    %tst;                                                                                                                               
                                                                                                                                        
    *_                                                                                                                                  
    | | ___   __ _                                                                                                                      
    | |/ _ \ / _` |                                                                                                                     
    | | (_) | (_| |                                                                                                                     
    |_|\___/ \__, |                                                                                                                     
             |___/                                                                                                                      
    ;                                                                                                                                   
    MPRINT(TST):   data _null_;                                                                                                         
    SYMBOLGEN:  Macro variable I resolves to 268435455                                                                                  
    MPRINT(TST):   array gb2[268435455] 8. _temporary_;                                                                                 
    SYMBOLGEN:  Macro variable I resolves to 268435455                                                                                  
    MPRINT(TST):   put "268435455";                                                                                                     
    MPRINT(TST):   run;                                                                                                                 
                                                                                                                                        
    MAX 268435455                                                                                                                       
                                                                                                                                        
    NOTE: DATA statement used (Total process time):                                                                                     
          real time           1.37 seconds                                                                                              
          user cpu time       0.73 seconds                                                                                              
          system cpu time     0.64 seconds                                                                                              
          memory              2097486.15k                                                                                               
          OS Memory           2113268.00k                                                                                               
          Timestamp           06/04/2020 12:47:39 PM                                                                                    
          Step Count                        126  Switch Count  0                                                                        
                                                                                                                                        
                                                                                                                                        
    MPRINT(TST):  quit;                                                                                                                 
                                                                                                                                        
    * __       _ _                                                                                                                      
     / _| __ _(_) |___                                                                                                                  
    | |_ / _` | | / __|                                                                                                                 
    |  _| (_| | | \__ \                                                                                                                 
    |_|  \__,_|_|_|___/                                                                                                                 
                                                                                                                                        
    ;                                                                                                                                   
                                                                                                                                        
    MLOGIC(TST):  %DO loop index variable I is now 268435456; loop will iterate again.                                                  
    MPRINT(TST):   data _null_;                                                                                                         
    SYMBOLGEN:  Macro variable I resolves to 268435456                                                                                  
    MPRINT(TST):   array gb2[268435456] 8. _temporary_;                                                                                 
    FATAL: Insufficient memory to execute DATA step program. Aborted during the COMPILATION phase.                                      
    ERROR: The SAS System stopped processing this step because of insufficient memory.                                                  
    NOTE: DATA statement used (Total process time):                                                                                     
          real time           0.01 seconds                                                                                              
          user cpu time       0.00 seconds                                                                                              
          system cpu time     0.01 seconds                                                                                              
          memory              330.28k                                                                                                   
          OS Memory           16112.00k                                                                                                 
          Timestamp           06/04/2020 12:47:39 PM                                                                                    
          Step Count                        127  Switch Count  0                                                                        
                                                                                                                                        
    SYMBOLGEN:  Macro variable I resolves to 268435456                                                                                  
    MPRINT(TST):   put "268435456";                                                                                                     
    MPRINT(TST):   run;                                                                                                                 
    MPRINT(TST):  quit;                                                                                                                 
    MLOGIC(TST):  %DO loop index variable I is now 268435457; loop will not iterate again.                                              
    MPRINT(TST):   run;                                                                                                                 
    MPRINT(TST):  quit;                                                                                                                 
    MLOGIC(TST):  Ending execution.                                                                                                     
                                                                                                                                        
                                                                                                                                        
