# utl-altair-personal-slc-exploded-text-using-workaround-to-submit-r-python-inside-slc-macro
Altair personal slc exploded text using workaround to submit r python inside slc macro
    %let pgm=utl-altair-personal-slc-exploded-text-using-workaround-to-submit-r-python-inside-slc-macro;

    %stop_submission;

    Altair personal slc exploded text using workaround to submit r python inside slc macro

    Too long to post on a listserv, see github

    github
    https://github.com/rogerjdeangelis/utl-altair-personal-slc-exploded-text-using-workaround-to-submit-r-python-inside-slc-macro

    Atair and SAS do not allow a macro to contain 'proc r' or 'proc python' code.

    There is a simpler solution using the student or commecial versions of the altair slc.
    Both the student and commecial versions support my submit r and pyhton macros.
    Both support the command like.

    I tried to add a menu item to eclipse toolbar that you could click on and it would ask you
    copy the exploded text to the windows clipboard.

    The workaround is to create a file that has your proc r or proc python code and
    '%include' the file inside the macro.



    PROBLEM (CREATE THIS EXPLODED TEXT)
    YOU NEED XPY MACRO IN YOUR AUTOCALL LIBRARY
    -------------------------------------------

    Usage %xpy(roger);

    The windows clipboard will have this text.
    You can paste it anywhere you want.

    It will also appear in the listing window.

    /*
     _ __ ___   __ _  ___ _ __
    | `__/ _ \ / _` |/ _ \ `__|
    | | | (_) | (_| |  __/ |
    |_|  \___/ \__, |\___|_|
               |___/
    */

    STEPS

      1 Create this template file (one time only)

        Note the '::::':  The text to explode will replace '::::'.

        options set=PYTHONHOME "D:\python310";
        proc python;
        submit;
        import sys;
        from pyfiglet import figlet_format
        txt=figlet_format("::::", font="standard")
        print(txt)
        with open("c:/temp/xpy2.sas","w") as f:
             f.write(txt)
        endsubmit;
        run;quit;

      2 Create macro xpy() that will
        Substitute 'yourtest' for '::::' and create
        an updated temp file. Finally include the proc python code.
        Make sure yo save macro xpy in your autocall library
        after you test.

        %macro procpy(text);

        filename tmp temp;
        data _null_;
          infile "c:/temp/xpy1.sas";
            file  tmp;
          input;
          _infile_=tranwrd(_infile_,'::::',"&text");
          put _infile_;
          putlog _infile_;
        run;quit;

        %include tmp;

        %mend procpy;


      3 Usage submit this slc program

        %xpy(roger)

    The workaround is to create a file that has your proc r or proc python code and
    '%include' the file inside the macro.


    /*                       _         _                       _       _
    / |   ___ _ __ ___  __ _| |_ ___  | |_ ___ _ __ ___  _ __ | | __ _| |_ ___
    | |  / __| `__/ _ \/ _` | __/ _ \ | __/ _ \ `_ ` _ \| `_ \| |/ _` | __/ _ \
    | | | (__| | |  __/ (_| | ||  __/ | ||  __/ | | | | | |_) | | (_| | ||  __/
    |_|  \___|_|  \___|\__,_|\__\___|  \__\___|_| |_| |_| .__/|_|\__,_|\__\___|
                                                        |_|
    */

    /*--- create a onetime slc sas program template to be used to create exploded text ---*/

    data _null_;
     file "c:/temp/xpy_template1.sas";
     input;
     put _infile_;
     putlog _infile_;
    cards4;
    options set=PYTHONHOME "D:\python310";
    proc python;
    submit;
    import sys;
    from pyfiglet import figlet_format
    txt=figlet_format("::::", font="standard")
    print(txt)
    with open("c:/temp/xpy_explode.txt","w") as f:
         f.write(txt)
    with open("c:/temp/xpy_explode.txt", "a") as f:
        f.write("!!!!\n")
    endsubmit;
    run;quit;
    ;;;;
    run;quit;

    /*
     _
    | | ___   __ _
    | |/ _ \ / _` |
    | | (_) | (_| |
    |_|\___/ \__, |
             |___/
    */

    2578      data _null_;
    2579       file "c:/temp/xpy_template1.sas";
    2580       input;
    2581       put _infile_;
    2582       putlog _infile_;
    2583      cards4;

    NOTE: The file 'c:\temp\xpy_template1.sas' is:
          Filename='c:\temp\xpy_template1.sas',
          Owner Name=T7610\Roger,
          File size (bytes)=0,
          Create Time=11:53:58 Oct 22 2025,
          Last Accessed=16:20:20 Oct 22 2025,
          Last Modified=16:20:20 Oct 22 2025,
          Lrecl=32767, Recfm=V

    options set=PYTHONHOME "D:\python310";
    proc python;
    submit;
    import sys;
    from pyfiglet import figlet_format
    txt=figlet_format("::::", font="standard")
    print(txt)
    with open("c:/temp/xpy_explode.txt","w") as f:
         f.write(txt)
    with open("c:/temp/xpy_explode.txt", "a") as f:
        f.write("!!!!\n")
    endsubmit;
    run;quit;
    NOTE: 13 records were written to file 'c:\temp\xpy_template1.sas'
          The minimum record length was 80
          The maximum record length was 80
    NOTE: The data step took :
          real time : 0.002
          cpu time  : 0.000


    2584      options set=PYTHONHOME "D:\python310";
    2585      proc python;
    2586      submit;
    2587      import sys;
    2588      from pyfiglet import figlet_format
    2589      txt=figlet_format("::::", font="standard")
    2590      print(txt)
    2591      with open("c:/temp/xpy_explode.txt","w") as f:
    2592           f.write(txt)
    2593      with open("c:/temp/xpy_explode.txt", "a") as f:
    2594          f.write("!!!!\n")
    2595      endsubmit;
    2596      run;quit;
    2597      ;;;;
    2598      run;quit;

    /*___                        _
    |___ \    ___ _ __ ___  __ _| |_ ___   _ __ ___   __ _  ___ _ __ ___
      __) |  / __| `__/ _ \/ _` | __/ _ \ | `_ ` _ \ / _` |/ __| `__/ _ \
     / __/  | (__| | |  __/ (_| | ||  __/ | | | | | | (_| | (__| | | (_) |
    |_____|  \___|_|  \___|\__,_|\__\___| |_| |_| |_|\__,_|\___|_|  \___/

    */

    %macro xpy(text);

    %utlfkil(c:/temp/xpy_explode.txt);

    title;
    footnote;

    filename tmp1 "c:/temp/xpy_template1.sas";
    filename tmp2 temp;

    data _null_;
      infile  tmp1;
        file  tmp2;
      input;
      _infile_=tranwrd(_infile_,'::::',"&text");
      put _infile_;
      putlog _infile_;
    run;quit;

    %include tmp2;

    /*--- clear clipboard sort of ---*/
    filename clipbrd clipbrd;
    data _null_;
      file clipbrd;
      put '';   /* Empty string */
    run;
    filename clipbrd clear;

    filename __dm clipbrd ; /*--- python c:/temp/xpy_explode.sas ---*/

    data _null_;
      infile "c:/temp/xpy_explode.txt";
      file __dm;
      input;
      select;
        when (_n_=1)            do; put @1 '/*';  putlog @1 '/*';  end;
        when (_infile_=:'!!!!') do; put @1 '*/';  putlog @1 '*/';  end;
        otherwise               do; put _infile_; putlog _infile_; end;
      end;
    run;

    filename __dm clear;

    %mend xpy;

    %xpy(roger);


    OUTPUT IN THE CLIPBOARD
    -----------------------

    /*
     _ __ ___   __ _  ___ _ __
    | `__/ _ \ / _` |/ _ \ `__|
    | | | (_) | (_| |  __/ |
    |_|  \___/ \__, |\___|_|
               | ___/
    */

    IN THE LOG WINDOW
    -----------------

    /*
     _ __ ___   __ _  ___ _ __
    | '__/ _ \ / _` |/ _ \ '__|
    | | | (_) | (_| |  __/ |
    |_|  \___/ \__, |\___|_|
               |___/
    */

    2452
    2453
    2454      %macro xpy(text);
    2455
    2456      %utlfkil(c:/temp/xpy_explode.txt);
    2457
    2458      title;
    2459      footnote;
    2460
    2461      filename tmp1 "c:/temp/xpy_template1.sas";
    2462      filename tmp2 temp;
    2463
    2464      data _null_;
    2465        infile  tmp1;
    2466          file  tmp2;
    2467        input;
    2468        _infile_=tranwrd(_infile_,'::::',"&text");
    2469        put _infile_;
    2470        putlog _infile_;
    2471      run;quit;
    2472
    2473      %include tmp2;
    2474
    2475      /*--- clear clipboard sort of ---*/
    2476      filename clipbrd clipbrd;
    2477      data _null_;
    2478        file clipbrd;
    2479        put '';   /* Empty string */
    2480      run;
    2481      filename clipbrd clear;
    2482
    2483      filename __dm clipbrd ; /*--- python c:/temp/xpy_explode.sas ---*/
    2484
    2485      data _null_;
    2486        infile "c:/temp/xpy_explode.txt";
    2487        file __dm;
    2488        input;
    2489        select;
    2490          when (_n_=1)            do; put @1 '/*';  putlog @1 '/*';  end;
    2491          when (_infile_=:'!!!!') do; put @1 '*/';  putlog @1 '*/';  end;
    2492          otherwise               do; put _infile_; putlog _infile_; end;
    2493        end;
    2494      run;
    2495
    2496      filename __dm clear;
    2497
    2498      %mend xpy;
    2499
    2500      %xpy(roger);

    NOTE: The infile tmp1 is:
          Filename='c:\temp\xpy_template1.sas',
          Owner Name=T7610\Roger,
          File size (bytes)=1066,
          Create Time=11:53:58 Oct 22 2025,
          Last Accessed=16:05:29 Oct 22 2025,
          Last Modified=16:05:29 Oct 22 2025,
          Lrecl=32767, Recfm=V

    NOTE: The file tmp2 is:
          Filename='d:\wpswrk\_TD31536\#LN00041',
          Owner Name=T7610\Roger,
          File size (bytes)=0,
          Create Time=16:16:52 Oct 22 2025,
          Last Accessed=16:16:52 Oct 22 2025,
          Last Modified=16:16:52 Oct 22 2025,
          Lrecl=32767, Recfm=V

    options set=PYTHONHOME "D:\python310";
    proc python;
    submit;
    import sys;
    from pyfiglet import figlet_format
    txt=figlet_format("roger", font="standard")
    print(txt)
    with open("c:/temp/xpy_explode.txt","w") as f:
         f.write(txt)
    with open("c:/temp/xpy_explode.txt", "a") as f:
        f.write("!!!!\n")
    endsubmit;
    run;quit;
    NOTE: 13 records were read from file tmp1
          The minimum record length was 80
          The maximum record length was 80
    NOTE: 13 records were written to file tmp2
          The minimum record length was 80
          The maximum record length was 81
    NOTE: The data step took :
          real time : 0.003
          cpu time  : 0.000


    Start of %INCLUDE(level 1) tmp2 is file d:\wpswrk\_TD31536\#LN00041
    2501    +  options set=PYTHONHOME "D:\python310";
    2502    +  proc python;
    2503    +  submit;
    2504    +  import sys;
    2505    +  from pyfiglet import figlet_format
    2506    +  txt=figlet_format("roger", font="standard")
    2507    +  print(txt)
    2508    +  with open("c:/temp/xpy_explode.txt","w") as f:
    2509    +       f.write(txt)
    2510    +  with open("c:/temp/xpy_explode.txt", "a") as f:
    2511    +      f.write("!!!!\n")
    2512    +  endsubmit;

    NOTE: Submitting statements to Python:


    2513    +  run;quit;
    NOTE: Procedure python step took :
          real time : 0.834
          cpu time  : 0.000



    NOTE: The file clipbrd is:
          Clipboard

    NOTE: 1 record was written to file clipbrd
          The minimum record length was 1
          The maximum record length was 1
    NOTE: The data step took :
          real time : 0.002
          cpu time  : 0.000



    NOTE: The infile 'c:\temp\xpy_explode.txt' is:
          Filename='c:\temp\xpy_explode.txt',
          Owner Name=T7610\Roger,
          File size (bytes)=180,
          Create Time=15:55:34 Oct 22 2025,
          Last Accessed=16:16:53 Oct 22 2025,
          Last Modified=16:16:53 Oct 22 2025,
          Lrecl=32767, Recfm=V

    NOTE: The file __dm is:
          Clipboard

    /*
     _ __ ___   __ _  ___ _ __
    | '__/ _ \ / _` |/ _ \ '__|
    | | | (_) | (_| |  __/ |
    |_|  \___/ \__, |\___|_|
               |___/
    */
    NOTE: 7 records were read from file 'c:\temp\xpy_explode.txt'
          The minimum record length was 4
          The maximum record length was 27
    NOTE: 7 records were written to file __dm
          The minimum record length was 2
          The maximum record length was 27
    NOTE: The data step took :
          real time : 0.004
          cpu time  : 0.015

    /*
                    _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */


