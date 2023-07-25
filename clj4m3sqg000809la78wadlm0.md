---
title: "Navigating Maps in GO & other $(Imp.) Basics"
seoTitle: "Navigating Maps in GO & other $(Imp.) Basics"
datePublished: Tue Jun 20 2023 18:21:43 GMT+0000 (Coordinated Universal Time)
cuid: clj4m3sqg000809la78wadlm0
slug: navigating-maps-in-go-other-imp-basics
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687193656630/6c0daabb-5a8b-414a-823c-0b21c62c592a.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1687285282153/45bfe4e5-e26f-40af-a824-c7fb6b19ff05.png
tags: go, technology, google, 2articles1week, wemakedevs

---

In order to understand the basics of Maps, packages, testing, interface, RCP and a lot more we need to clear up the basics of this language to master it eventually. So in this blog, we will be focussing more on the basics like arrays, slices, Maps, functions, closure and Recursion.

If you want to understand the power and Basics of this amazing language **GO** please read my blog in which I have discussed all of its amazing features and immense success.

%[https://codechill.hashnode.dev/unveiling-the-power-of-go-why-googles-go-language-is-taking-over-the-tech-world] 

# Arrays and Slices

## Arrays

An array is a numbered sequence of elements of a single type with a fixed length. in Go they look like:-

```go
package main

import "fmt"

func main(){
var x [5] float64
x[0] = 98
x[1] = 63
x[2] = 82
x[3] = 78
x[4] = 56

var total float64 = 0
for i := 0; i < len(x); i++{
       total += x[i]
}
fmt.println(total / len(x))
}
```

As we can see that instead of writing 5 in the code we entered len(x) instead in the code, but if we would have introduced 5 then, we would have shown up red flags.

This code is been initialized correctly but as the code reaches up to the sumation of all the elements in the array, we will encounter an error due to the difference in the data type in the total and len(x) wihc can be resolved by

```go
package main

import "fmt"

func main(){
x :=[5]float64{
x[0] = 98
x[1] = 63
x[2] = 82
x[3] = 78
x[4] = 56
}
var total float64 = 0
for i := 0; i < len(x); i++{
       total += x[i]
}
fmt.Println(total / float64(len(x)))
}
```

Here in this amended code, we introduced ":" which is similar to that in c language which represents variables apart from this mere change the array is been arranged in a much better way and the type of len(x) is been changed to float64.

### Use of (\_) underscore

```go
var total float64 = 0
for _, value := range x {
     total += value
}
fmt.Println(total/ float64(len(x)))
```

In Go we aren't allowed to create a variable that is never used. A single underscore(\_) is used to tell the compiler that we don't need the indicated variable.

## Slices

A slice is a segment of an array. Like an array, slices are indexable as well and have a length. Unlike arrays, this length is allowed to change.

This creates an associated with an underlying float64 array of length 5. Slices are always associated with some array, and although they can never be larger than the array but can be smaller.

```go
x := make([]float64, ,5 10)
```

This is an example of a slice of length 5 and capacity 10.

```go
arr := [5]float64{1, 2, 3, 4, 5}
x := arr[1:4]
```

This creates a slice out of an array named "arr" where low is the index where the slice starts and high is the index of where to end it(but not including the index itself). According to this example, the output would bring up a slice "x" as \[2,3,4\] from the array "arr".

For convenience, we are also allowed to omit low, high or even both low and high. arr\[0:\] would bring up the entire array in the slice starting from 0 while arr\[:5\] is the same as arr\[0:5\] which will print numbers from the index number 0 to 4(not including the high itself ).

Now, in addition to the indexing parameter, Go includes two built-in functions to assist with slices: append and copy.

### append()

append adds an element at the end of the slice. If there is sufficient capacity in the underlying array the element is placed at the end of the slice and the length is increased. However, if there is not enough space available in the slice then a new slice is created where all of the existing elements are copied over.

```go
func main(){
   slice1 := []int{1, 2, 3}
   slice2 := append(slice1, 4, 5)
   fmt.Println(slice1, slice2)
}
```

Here in this example, slice2 is been arranged to get appended with slice1 and include 4 and 5 as well.

### copy()

copy takes two arrangements: dst and src. All of the entries in src are copied into dst overwriting whatever is there. If the length of two slices is two slices are not the same, the smaller of the two will be used.

```go
func main(){
    slice1 := []int{}1, 2, 3
    slice2 := make([]int, 2)
    copy(slice1, slice2)
    fmt.Println(slice1, slice2)
}
```

Here in this function, we have slice1 containing {1, 2, 3} as its indices and the slice2 is made by using the make keyword also specifying its type and the size of the slice. As a result, slice2 is produced copying all the contents of slice1 but, since the size of slice2 is set to be limited to 2 that why only 2 elements of slice1 are copied to slice2.

Slices are typically used to represent a list of items when you need to access the nth item quickly. For example, if you want to access or search for a particular entry that is not an integer(say a float, char or maybe some other data type).

# Maps

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687265392699/fdd09d37-4a38-4155-8413-d3fe6924ed58.png align="center")

A **map** is an unordered collection of key-value pairs which are also sometimes called associative arrays, hash tables, or dictionaries.

Maps are often looked up as a value by their associated keys. The Map is represented by the keyword **map**, followed by the key type in brackets and finally the value type. If you were to read this out loud, you would say "x is a map of strings to ints".

Like an array, maps can also be accessed using brackets.

```go
x := map[string]int
x["key"] := 10
fmt.Println(x["key"])
```

If we would have simply requested to give print the value of a key by simply writing x in place of x\["key"\] we would have encountered compile run time error( As the name suggests runtime errors happen when you run the program, while the compile time error happens when you try to compile the program). It is also compulsory for the program to be initialized before they are used as we did in the first line. We can also create a map with another key type as well like int, float, or anything else as well.

**Similarities of Map with an array**

Map does look very much similar to an array but the main difference is

1. the length of a Map can change as we add a new item to it. When initially created, it has a length of 0 but as soon we add(let's say) x\[1\] = 10 to it then the length of the Map increases to 1 and so on.
    
2. Maps are not sequential which means when we add some element in a Map it may go with x\[1\] but in array, it must go sequentially with x\[0\] but maps don't have that requirement.
    

Labeling out every line with the name of the map and then its key could be a bit more of a tedious work so instead we can simply write it in a much-comprised form can surely bring us some more time.

```go
package main

import "fmt"

func main(){
elements := map
   "H": "Hydrogen",
   "He": "Helium",
   "Li": "Lithium",
   "Be": "Beryllium",
   "B": "Boron",
   "C": "Carbon",
}
```

Adding up certain information as well with the name can bring up all the required information in one place and increase up the efficiency of the code.

```go
func main(){
elements := map[string]map[string]string{
     "H": map[string]string{
          "name":"Hydrogen",
          "state":"gas",
    },
     "He": map[string]string{
          "name":"Helium",
          "state":"gas",
    },
     "Li": map[string]string{
          "name":"Lithium",
          "state":"solid",
    },
     "Be": map[string]string{
          "name":"Beryllium",
          "state":"solid",
    },
     "B": map[string]string{
          "name":"Boron",
          "state":"solid",
    },
     "C": map[string]string{
          "name":"Carbon",
          "state":"solidH",
    },
  }
if el, ok := elements["Li"]; ok{
      fmt.Println(el["name"], el["state"])
  }
}
```

According to the element of a map can return two values instead of just one. The first value is the result of the lookup, the second tells whether or not the lookup was successful.

Which looked like the code we entered in the last of our code in which we get the value from the map. then, if it's successful, we run the code inside the block.

Notice that the type of the map has changed from map\[string\]string to map\[string\]map\[string\]string. We now have a map of strings to strings. The outer map is used as a lookup table used as a lookup table based on the element's symbol, while the inner maps are used to store general information about the elements. `map[string]map[string]string` in Go represents a nested map structure. It is a map where the keys are of type string, and each corresponding value is another map with string keys and string values.

In this nested map structure, the outer map is indexed by strings, and each value associated with a key in the outer map is an inner map. The inner map, in turn, is also indexed by strings, and each value associated with a key in the inner map is a string.

# Functions

A function also known as a procedure or a subroutine is an independent section of code that maps zero or more input parameters to zero or more output parameters. We generally know about what functions do so we will skip up to the main structure and different elements of features.

## Functions from the call stack

```go
func main() {
      fmt.Println(f1())
}
func f1(){
       return f2()
}
func f2(){
       return 1
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687279897810/c84eb002-6c4d-430f-885d-a23f0f77f58a.png align="center")

each time we call a function we push it onto the call stack, and each time we return from a function, we pop the last function off the stack.

### multiple values in Go

Go is capable of returning multiple values from a function.

```go
func f(){
return 5, 6
}
func main(){
x, y := f()
}
```

Change the return types to contain multiple types separated by a comma, change the expression after the return so that it contains multiple comma-separated expressions, and finally, change the assignment statement so that multiple values are on the left side of the:= or =. Multiple values are often used to return an error value along with the result (x, err:=f()), or a boolean to indicate success (x, ok := f())

## Variadic functions

add is allowed to be called with multiple integers. This is known as a variadic parameter.

```go
func add(args...int) int {
   total := 0
   for _, v := range args{
   total += v
   }
  return total
}
func main(){
   fmt.Println(add()1, 2, 3)
}
```

By using an ellipsis (...) before the type name of the last parameter, you can indicate that it takes zero or more of those parameters. In this case, we take or more ints. We invoke the function like any other function except we can pass as many ints as we want.

We can also pass a slice of ints by following the slice with ellipses:

```go
fucn main(){
   xs := []int{1, 2, 3}
   fmt.Println(add(xs...))
}
```

The Vardiac function in go language is similar to that in VarArgs Java if you know about it, where we can use any number of parameters in the code and in that as well we use the ellipses(...).

```java

//Variable Length Arguments  is used when we don't  know how many inputs we are giving

import java.lang.reflect.Array;
import java.util.Arrays;
  public class VarArgs {
    public static void main(String[] args) {
        //  fun(3,56,3453,34,76,3,65,56,7);       //So here  it will arrange these integers into the form of array
                                                    //If we would left it nothing in the box then also it will still run  and will give an empty array
          multiple(34,56,"Aryan","Aditya","Suraj","Shashank");
          demo(45,67,234);
    }

    static void demo(int...v){
        System.out.println(Arrays.toString(v));
    }
                        // Now here if the funtion is left empty then it now give an error and it is called as the
                       //AMBIGUITY as we didn't made any hints to which function we actually refering to and thus it is giving an error
    static void demo(String...v){
        System.out.println(Arrays .toString(v));
    }

      static void multiple(int a, int b, String...v){         //Specifies ad the first two ones are integers and then exist string data type

    //static void fun(int...v){                          //Here it totally depends upon us wheather we want to put integer or char or any other kind
        System.out.println(Arrays.toString(v));                      //of string into array.
    }
  }
```

Which will on running give result as:--

`[Aryan, Aditya, Suraj, Shashank]`

`[45, 67, 234]`

## Closure

It is possible to create functions inside of functions. A function like this together with the nonlocal variable it references is known as a closure. One way to use closure is by writing a fucntion that returns another function, which when called, can generate a sequence of numbers.

```go
func makeEvenGenerator() func() uint{
   i := uint(0)
   return func() (ret uint){
     ret = i
     i += 2
     return
   }
}
func main(){
nextEven := makeEvenGenerator()
   fmt.Println(nextEven())
   fmt.Println(nextEven())
   fmt.Println(nextEven())
}
```

makeEvenGenerator returns a function that generates even numbers. Each time it's called, it adds 2 to the local i variable, which -unlike normal local variables-persists between calls.

# Recursion

A function is able to call itself. Here is one way to compute the factorial of a number:

```go
func facorial(){
   if x === 0{
   return 1
  }
   return x * factorail(x-1)
}
```

## defer, panic, and recover

### defer

defer that schedules a function call to be run after the function completes.

```go
package main()

import "fmt"

func first(){
   fmt.Println("1st")
}
func second(){
   fmt.Println("1st")
}
func main(){
   defer second()
   first()
}
func main(){
   first()
   second()
}
```

In this program, defer will make the second() function to be called in the end that is after the execution of the first() function.

defer is often used when resources need to be freed in some way. We might like to close a file after opening it with the help of defer function.

```go
f, _ := os.Open(filename)
defer f.Close()
```

## panic and recover

We created a function called the panix=c function to cause a runtime error. We can handle a runtime panic with the built-in recover function. recover stops the panic and returns the value that was passed to the call to panic.

```go
package main

import "fmt"

func main(){
defer func(){
str := recover()
fmt.println(str)
}()
panic("PANIC")
}
```

A panic generally indicates a programming error like attempting to access an index of an array that's out of bounds, forgetting to initialize a map, etc or an exceptional condition that there's no easy to recover from, as a result of which it is been names panic.

Thanks for reading my blog hope, I keep up the sharing in public motto and share my learnings 😄😄.

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile: [Aryan\_2407](https://twitter.com/Aryan_2407)

Soon, i will be bringing up another blog on structs, interfaces, pacakges, Hashes & cryptography, Concurrency and a lot more concepts with better explanations to make this road of understanding as frictionless as possible. Hope you learned what you came here to understand.