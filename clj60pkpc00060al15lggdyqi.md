---
title: "Packaging 101: The  art of packaging in GO"
seoTitle: "Packaging 101: The  art of packaging in GO"
seoDescription: "In this blog, I will be discussing about the packages and its different components in Go and how does it effects our production"
datePublished: Wed Jun 21 2023 17:58:20 GMT+0000 (Coordinated Universal Time)
cuid: clj60pkpc00060al15lggdyqi
slug: packaging-101-the-art-of-packaging-in-go
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687321899723/0a3eec94-b24b-4967-a420-e5d985463c25.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1687370094078/53b71f74-b252-4124-b154-5fba1c3428c9.jpeg
tags: go, technology, 2articles1week, technical-writing-1, wemakedevs

---

In order to understand Packages in Go, it is important to get a basic knowledge of Methods & Interfaces first, so in this blog, we will be discussing about Methods, Interfaces, Packages and containers in GO.

In Case you are just starting up with learning about GO please go check out my some previous blogs on Go

%[https://codechill.hashnode.dev/unveiling-the-power-of-go-why-googles-go-language-is-taking-over-the-tech-world] 

%[https://codechill.hashnode.dev/navigating-maps-in-go-other-imp-basics] 

# Methods

```go
package main

import ("fmt"; "math")

func circleArea(c Circle)float64{
   return math.Pi * c.r * c.r
}
func main(){
c := Circle{0, 0, 5}
fmt.Println(circleArea(&c))
}
```

It is a general function circleArea being used in this program to calculate the area of the circle in which the fields are used using the .operator.

The &(AND) operator is used while calling the circleArea function to use it as a pointer to the function which is done as the arguments in GO are copied and if we would have attempted to modify one of the fields inside the circleArea function, it wouldn't have modified the original variable.

**Now using Methods in the code:**

Method helps in reducing the size of the code to a much compact form as:--

```go
func (c *Circle) area() float64{
     return math.Pi * c.r*c.r
}
```

In between the keyword func and the name of the function, we've added a *receiver*. The receiver is like a parameter--it has a name and a type--but by creating the function in this way, it allows us to call the function using the .operator;

`fmt.Println(c.area())`

Go automatically knows to pass a pointer to the circle for this method as a result of which the &(AND) operator isn't needed in this case.

# Embedded Types

A struct's fields usually represent the has- a relationship.

```go
type Animal struct{
   Name name
   Type string
}
func (a *Animal)Talk(){
   fmt.Println("Its name is", a.Name)
}
```

This would work, but we would instead say animal is a name rather than an animal has a name. Go supports relationships like this using embedded types which are often referred to as anonymous fields as:--

```go
types Animal struct{
   Name
   Type string
}
```

Here we instead just gave the type and didn't gave the name to the particular type and thus the Name can be accessed using the type name.

# Interface

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687351132415/8029e992-cc30-473d-af3e-9b4de7c8419e.png align="center")

Go has a way of making these accidental similarities explicit through a type known as an interface.

```go
type Area interface{
   area() float64
}
```

Like a struct, an interface is created using the type keyword followed by the name of the interface and then the keyword interface. But instead of defining fields, we define a method set. A method set is a list of methods that a type must have in order to implement the inner face.

We can try it up by calculating the area of a rectangle and a circle by using the interface.

```go
func totalArea(circles ...Circle, rectangle ...Rectangle)float64{
   var area float64
   for _, c := range circles {
     total += c.area()
  }
   for _, r := range rectangle{
     total += r.area()
   }
   return total
}
```

In spite of using circles ...Circle and rectangle ...rectangle in the bracket along with the totalArea function we could have used circles \[\]Circle and rectangle \[\]Rectangle in the bracket in the function totalArea.

This will raise an issue whenever we raise a third parameter for this function like a polygon or some square and thus we will have to change our function to handle it.

To solve this problem, we can is instead consider a MultiShape that is made up of several smaller shapes:

```go
type MultiShape{
   shapes := []Shape{
     Circle{0, 0, 5},
     Rectangle{0, 0, 10, 10}
   },
}
func (m * MultiShape) area() float64{
     var area float64
     for _, s := range m.shapes{
        area += s.area()
     } 
   return area
}
```

Interfaces are particularly useful in software projects and become more complex. They allow us to hide the incidental details of the implementation. In the example as long as the area method continues to produce some results, we are free to change how a CIrcle or Rectangle is structured without having to worry about whether or not the totalArea function will continue to work.

**GO also has a mechanism for combining functions, structs, interfaces and variables together into a single component known as a package.**

# Package

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687351043993/001f8031-7893-4bd2-b88a-f138fade3501.png align="center")

Package helps in organizing the data in your code making it easier for you to find and reuse the code with a lesser chance of overlapping between the names thus reducing our code and passing up the speed of production.

Packages facilitate code reuse by allowing you to import and utilize functionality from other packages. With packages, you can easily leverage existing solutions and libraries, avoiding reinventing the wheel and saving development time.

Now we might find out a lot of packages we use in our everyday code without actually getting to know what they do and how they affect the production

### fmt

It is most commonly used package for managing our code in the most descent and productive way:-

1. it reduces the chance of overlapping between the name thus keeps our function name short and succinct
    
2. It organizes code so that it's easier to find code you want to reuse.
    
3. It seeps up the compiler by only requiring the recompilation of smaller chunks of a program.
    

### Strings

This is for managing strings in Go, and includes a large number of functions to work with strings in the string package such as counting up the length of a string, searching up the prefix or suffix and a lot more functions helping out in managing data in code in various forms. here are some of the functions by which you can manage your data in a much better way by strings package

1. To search for a smaller string in a bigger one, use the `Contains` function:
    
    ```go
    package main
    
    import (
    "fmt"
    "strings"
    )
    func main(){
    fmt.Println(strings.Conatins("test", "es"))
    }
    ```
    
2. To count the number of times a smaller string occurs in a bigger string, use the `Count` function:
    
    ```go
    package main
    
    import (
    "fmt"
    "strings"
    )
    func main(){
    fmt.Println(strings.Count("test", "t"))}
    ```
    
3. To determine if a bigger string starts with a smaller string, use the `HasPrefix` function:
    
    ```go
    package main
    
    import (
    "fmt"
    "strings"
    )
    func main(){
    fmt.Println(strings.hasPrefix("test", "te"))}
    ```
    
4. To determine if a bigger string ends with a smaller string, use the `HasSuffix` function:
    
    ```go
    package main
    
    import (
    "fmt"
    "strings"
    )
    func main(){
    fmt.Println(strings.HasSuffix("test", "st"))}
    ```
    
5. To find the position of a smaller string in a bigger one, use the `Index` function which returns -1 if the string isn't founded
    
    ```go
    package main
    
    import (
    "fmt"
    "strings"
    )
    func main(){
    fmt.Println(strings.Index("test", "e"))
    // =>1
    }
    ```
    
6. To take a list of strings and join them together in a single string separated by another string, use the `Join` function
    
    ```go
    package main
    
    import (
    "fmt"
    "strings"
    )
    func main(){
    fmt.Println(strings.Join([]string({"a", "b"}, "-")))
    // => "a-b"
    }
    ```
    
    Similarly, the string function can be used to use it as
    
    `Repeat` To repeat a string up to the number of times it has been command to do
    
    `Replace` To replace a smaller string in a bigger one with some other smaller one
    
    `Split` To split a string into a list of strings by separating strings like a comma `ToUpper` To convert a string to all uppercase letters
    
    `ToLower` To convert a string to all lowercase letters
    

## Go's io package

Go's io package consists of a few functions and interfaces with two main interfaces reader and Writer. Reader supports reading by the Read method and Writer supports writing by Write method. To support these functions and interfaces sometimes it is important to open up the file first and that's where the `os` package comes into the frame.

## os Package

To open a file in Go, use the open function from the os package. To read a file and display them onto the terminal we can write up the code in such way:

```go
package main

import {
"fmt"
"os"
}

func main(){
file, err := oss.Open("test.txt")
if err != nil{
//handle the error here
return
}
defer file.Close()

//get the file size
stat, err := file.Stat()
if err != nil{
return
}

//read the file 
bs := make([]byte, stat.Size())
_, err != nil{
return
}

str := string(bs)
fmt.Println(str)
}
```

Here is the code working cycle :-

1. `os` package is imported to work with operating system-related functionalities.
    
2. In the `main` function, the code attempts to open a file named "test.txt" using [`os.Open`](http://os.Open) and assigns the result to the `file` variable. If an error occurs during the file opening process, it is handled, and the function returns.
    
3. After successfully opening the file, the code uses the `defer` keyword to ensure that the file is closed after reading its content. This is done to release resources associated with the file when the function finishes executing, whether it completes successfully or encounters an error.
    
4. Next, the code uses the `Stat` method of the `file` variable, which returns a `FileInfo` value. `FileInfo` is an interface in the `os` package that provides information about a file.
    
5. If an error occurs during the `Stat` operation (e.g., the file does not exist), it is handled, and the function returns.
    
6. Assuming the `Stat` operation is successful, the code retrieves the file size from the `stat` variable using `stat.Size()`.
    
7. It then creates a byte slice (`bs`) with the size equal to the file size, in order to read the entire file content into memory.
    
8. The `Read` method is then called on the `file` variable, which reads the contents of the file into the byte slice `bs`. The number of bytes read and any potential error are returned, but the code snippet is missing the assignment to the `err` variable in this line: `_, err != nil{`. It should be `_, err =` [`file.Read`](http://file.Read)`(bs)`. The code as it is would produce a syntax error.
    
9. Finally, the code converts the bytes in `bs` to a string (`str`) and prints it to the console.
    

reading file is pretty easy so to do it there's an easy alternative instead:

```go
package main

import {
"fmt"
"io/ioutil"
}

func main(){
bs, err := iotil.ReadFile("text.txt")
if err != nil{
return
}
str := string(bs)
fmt.Println(str)
}
```

To create a file, use os.Create function. It takes the name of the file, creates it in the current working directory, and return an os.File and possibly an error if it was unable to create it for some reason.

```go
pacakge main

import{
"os"
}

func main(){
file, err := os.Create("test.txt")
if err!= nil{
//handle the error here
return
}
defer fiel.Close()

file.WritingString("test")
}
```

To get the contents of a directory, we use the same os.Open fucntion but give it a directory path instead of a file name. Then we call the Readdir method:

```go
pacakge main()

import {
"fmt"
"os"}

func main(){
dir, err := os.Open(".")
if err != nil{
return}
defer dir.Close()

fileInfos, err := dir.Readdir(-1)
if err != nil{
return}
for _, fi := rangeInfos{
fmt.println(fi.Name())
   }
}
```

Readdir takes a single argument that limits the number of entries returned.

Often we recursively walk a folder(read the folder's contents, all the folder's contents all the subfolder, all the sub- subfolders, etc). To make this easier, there's a `Walk` function provided in the path/filepath package:

```go
package main

import {
"fmt"
"os"
"path/filepath"
}
func main(){
filepath.Walk(".", func(path string, info os.File.Info, err error)error{
fmt.Println(path)
return nil
})
}
```

The function you pass to walk is called for every file and folder in the root folder(in this case, .). It's passed three arguments: path, which is the path to the file; info, which is the information for the file(the same information you get from using os.Stat); and err, which is any error that was received while walking the directory. The function returns and you can return `filepath.SkipDir` to stop walking immediately.

Hope you get to learn some out of this blog for which you came here for 😄

That was all in this blog soon, but if you still want to learn about making of tests which is highly used in the domain for testing up the code before pushing it to the production and is highly used in chaos engineering as well, then here is the blog for that:-

%[https://codechill.hashnode.dev/testing-in-go-increasing-efficiency-of-code] 

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile: [Aryan\_2407](https://twitter.com/Aryan_2407)