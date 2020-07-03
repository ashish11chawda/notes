<h1 id="heading-main">Programming in C++</h1>

<h2 id="introduction">Basic Introduction</h2> 

- Header file that need to be included for standard input/output is `<iostream>`.
    - It is used to stream input/output on console.
- Unlike C language, there's no need to put `.h` extension in the Preprocessor Directives.

- In C Language, all functions are of global namespace, but in C++, standard input/output are in `std` namespace so they need to be defined of which namespace they belong.
    - for example: `cin` and `cout` function in C++ can be written as
  
        ```cpp
        std::cin >> a;
        std::cout << a;
        ```
        > `::` is membership operator.
    - This hectic task can be reduced by using following statement
        ```cpp
        using namespace std;
        //now cin and cout can be written without std namespace
        cin >> a;
        cout << a;
        ```
- 
