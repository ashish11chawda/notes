# Data Structures

A program is a set of instructions which is performed on data in memory.

Data structures is how that data is organised in memory.

> Best programming language to learn coding data structures is C, C++ and Java.

## Essential Concepts of C and C++

<details>
<summary> <h3 style="display:inline;">Array</h3> </summary>

> Array is a collection of similar type of data items in a continuous manner.
> Indexing starts from `0` to `size - 1`.

It is created on Stack inside the memory.

```cpp
//declaring an array
int A[5];

//Inserting Elements
A[0] = 1;

//declaring and initializing an array
int B[]={1,2,3,4,5}
int size = 5;

//looping through an array
for(int i = 0; i < size-1; i++){
    cout << B[i];
}
```

</details>

<details>
<summary> <h3 style="display:inline;">Structures</h3> </summary>

> Collection of related data items of dissimilar type under one name.

Structure is used to define user defined data types from primitive data types or other user defined data types.

It is created in Stack frame of that function inside Memory.

```cpp
//declaring a structure
struct rectangle{
    int length; // 4 Bytes
    int breadth; // 4 Bytes
};
```

| length | breadth |
| -------|---------|
| 4 Bytes| 4 Bytes |

```cpp
// defining a structure variable
struct rectangle r;

// defining and initializing a structure variable
struct rectangle R = {5,10};
```

| length | breadth |
| -------|---------|
| 5      | 10      |

```cpp
//accessing a structure member using dot (.) operator
cout << "Area is " << R.length * R.breadth << endl;
```

Examples where a structure can be used:

- Complex Number
    - Real Part
    - Imaginary Part
- Student or Employee Information
    - Name
    - Roll no.
    - Department
- Book Information
    - Author
    - Publication
    - Release Date
- Playing Card
    - Face Value ( `1` to `10`, `11`(J), `12`(Q), `13`(K) )
    - Shape (`0`(Club), `1`(Spade), `2`(Diamond), `3`(Heart) )
    - Color (`0`(Red), `1`(Black) )
    - **Enum can be used to define Face, Shape and Color seperately**

```cpp
//defining a structure for card
struct card{
    int face;
    int shape;
    int color;
};

// defining a deck of cards using a array of structures
struct card deck[52];
```

</details>
<details>
<summary> <h3 style="display:inline;">Pointers</h3> </summary>

> Pointers are variables which store addresses of data variables.

Pointers are used to directly access the resources which are outside the program and accessing heap memory and also used for parameter passing.

```cpp
int a = 10; // data variable occupying 4 bytes of memory
int * ptr; // pointer or address variable
ptr = &a; // initializing pointer
int b = *ptr; // dereferencing a pointer for the data its pointing
```

</details>

## Intoduction

![Data Structure Intro](images/Data%20Structure%20Intro.png)

> Every Program deals with some data, that data needs to be brought inside main memory with program for execution of the program. The arrangement or organising of data inside main memory for efficient utilization by the application is called **Data Structure**.

In case of large scale data or commercial data(operational and legacy data), the arrangement of data in HDD or permanent storage is called Database.

> Operational Data is used on daily basis.

> legacy data is historical data which is kept on an array of disc which is **Data Warehouse**.
> Algorithms operating on legacy data are Data Mining Algorithms.

![Data Structure Intro](images/DSA%20Intro%202.png)

### Static and Dynamic Memory Allocation

#### Memory

Memory of larger sizes is divided into managable units called as segment.
Memory Segment is basically of 64KB *(spanning from 0 to 65535 bytes)* for memory of larger size.

> ![Data Structure Intro](images/Memory%20Segment.png)

