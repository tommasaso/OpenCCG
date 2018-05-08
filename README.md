OPENCCG
=======
OpenCCG, the OpenNLP CCG Library, is an open source natural language processing library written in Java, which provides parsing and realization services based on Mark Steedman's Combinatory Categorial Grammar (CCG) formalism.

---
Configurarion
-------------
1. JAVA_HOME: where java is installed on your computer:
    + For MacOS user:
        ```
        /usr/libexec/java_home
        ```
        the output of this command must be the path where your JAVA is installed.
        
        So now you neeed to `export` your `JAVA_HOME` in this way:
        ```
        export JAVA_HOME=/your_path
        ```

        Example:
        ```
        > /usr/libexec/java_home
        /Library/Java/JavaVirtualMachines/jdk-10.jdk/Contents/Home
        > export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-10.jdk/Contents/Home/
        ```
    + For Windows User:
        ```
        > for %i in (javac.exe) do @echo.   %~$PATH:i
        ```
        the output of this command must be the path where your JAVA is installed.
        So now you neeed to `SET` your `JAVA_HOME` in this way:
        ```
        SET JAVA_HOME=/your_path
        ```

        Example:
        ```
        > for %i in (javac.exe) do @echo.   %~$PATH:i
            C:\Program Files (x86)\Common Files\Oracle\Java\javapath\java.exe
        > SET JAVA_HOME=C:\Program Files (x86)\Common Files\Oracle\Java\javapath\java.exe
        ```
2. OPENCCG_HOME: where you put the OpenCCG files
    + For MacOS user:
        ```
        export OPENCCG_HOME=/Users/tommasaso/Documents/openccg
        ```
    + For Windows user
        ```
        SET OPENCCG_HOME=/Users/tommasaso/Documents/openccg
      ```

3. PATH: same as your original PATH, but also now including `$OPENCCG_HOME/bin`
    +  For MacOS user:
        ```
        export PATH=$OPENCCG_HOME/bin:$PATH
        ```
    + For Windows User:
        ```
        SET PATH=$OPENCCG_HOME/bin:$PATH
        ```
4. LD_LIBRARY_PATH:sameasyouroriginalLD_LIBRARY_PATH,butalsonowincludingOPENCCG_HOME/lib
    +  For MacOS user:
        ```
        export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OPENCCG_HOME/lib
        ```
    + For Windows User:
        ```
        SET LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OPENCCG_HOME/lib
        ```


To test all the variable that you have created:
+ For MacOS user you can use the command like: `echo $VARIABLE`

        > echo $JAVA_HOME
        /Library/Java/JavaVirtualMachines/jdk-10.jdk/Contents/Home/
+ For Windows user you can use the command like: `echo %VARIABLE%`

        > echo %JAVA_HOME%
        C:\Program Files (x86)\Common Files\Oracle\Java\javapath\java.exe

---
Building
-------------
Once you set the variables, go to your `OPENCCG_HOME` directory and type: `ccg-build`

+ For MacOS user:

        > cd $OPENCCG_HOME
        > cp $OPENCCG_HOME/bin/ccg-build $OPENCCG_HOME
        > ./bin/ccg-build

+ For Windows user

        > cd $OPENCCG_HOME
        > copy $OPENCCG_HOME/bin/ccg-build $OPENCCG_HOME
        > bin/ccg-build

The output should be something like that:

        > cd $OPENCCG_HOME
        > ./bin/ccg-build
        Buildfile: /Users/tommasaso/Documents/openccg/build.xml
            ...
        BUILD SUCCESSFUL
        Total time: 7 seconds

---
Basic testing
-------------
You should open the folder grammars/tony and run the program with the command `tccg`
+ For MacOS user:

        > cd $OPENCCG_HOME/grammars/tiny/
        > tccg
        Loading grammar from URL: file:/Users/tommasaso/Documents/Uny/OneDrive/Artificial/Test/openccg/grammars/tiny/grammar.xml
        Grammar 'tiny' loaded.

        Enter strings to parse.
        Type ':r' to realize selected reading of previous parse.
        Type ':h' for help on display options and ':q' to quit.
        You can use the tab key for command completion, 
        Ctrl-P (prev) and Ctrl-N (next) to access the command history, 
        and emacs-style control keys to edit the line.

        tccg> the blue policeman bought a DVD
        3 parses found.

        Parse 1: s : 
        @w3:action(buy ^ 
                    <tense>past ^ 
                    <Actor>(w2:person ^ policeman ^ 
                            <det>the ^ 
                            <num>sg ^ 
                            <Mod>(w1:state ^ blue)) ^ 
                    <Patient>(w5:thing ^ DVD ^ 
                            <det>a ^ 
                            <num>sg))
        tccg> 