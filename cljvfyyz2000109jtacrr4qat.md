---
title: "Unlocking the Potential and Creating Go Web Servers"
seoTitle: "Unlocking the Potential and Creating Go Web Servers"
seoDescription: "We will digging deep into the creation of web servers in Go and how beneficial it has been proved for Go in the tech world"
datePublished: Sun Jul 09 2023 12:59:47 GMT+0000 (Coordinated Universal Time)
cuid: cljvfyyz2000109jtacrr4qat
slug: unlocking-the-potential-and-creating-go-web-servers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688892378925/39341353-7c46-4e54-9844-62be9af6f9c6.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688907191865/412dfed8-ad53-4cff-aa76-c24bed45ec6c.jpeg
tags: blogging, go, technology, google, wemakedevs

---

Golang is one of the best languages known for its efficient performance and multithreading features which enable its users to use it while implementing various performance-driven features in their applications.

Created by Google in 2009 by its engineers after reviewing problems faced in the real world like waiting for another program to get compiled first to work on hte another one, as an initiative to solve these problems in a much more efficient way which eventually lead them in building a language that supports multithreading, concurrency, and performance under stress. Gaining a lot of importance in the Cloud-native world it became the popular choice for developers in building microservices. As a result of which several companies as well are heavily using it because of its seamless functionality and advantage. Some of the biggest companies which use it in their production work are:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688906415411/8474a0ef-a708-4935-86c3-2d2149debe3d.png align="center")

Golang helps in writing distributed applications in a relatively straightforward way which helps in the frictionless building of web servers and web services. Here in this blog, we will be looking at the common approaches to communicating between multiple computers: TCP servers, HTTP servers and RPC.

## TCP

Most of the time we are communicating on the internet it is directed by TCP protocol whether you are streaming video or movies on the internet or having a video chat with another person it is all governed by TCP (Transfer Control Protocol).

To create a TCP server we need to include the net package's listen function which takes a network type and an address and port to bind and returns a net. listener:

```go
type Listener interface {
  //Accept waits for and retruns the next connection to the listener.
  Accept() (c Conn, err error)

  //Close closes the listener. 
  //Any blocked Accept operations will be unlocked and retrun errors.
  Close() error

  //Addr returns the listener's network address.
  Addr() Addr
}
```

We then after having the Listener, call Accept, which waits for a client to connect and returns a net. Conn. A net.Conn implements the io.Reader and io.Writer interfaces, so we can read from it and write it to just like a file.

```go
package main

import(
"encoding/gob"
"fmt"
"net"
)

fucn server(){
    //listen on a port
    ln, err := net.listen("tcp", "8080")
    if err != nil{
      fmt.Println(err)
      return
    }
  for {
    //accept a connection
    c, err := ln.Accept()
    if err != nil{
      fmt.Println(err)
      continue
    }
    //handle the connection
    go handServerConnection(c)
  }
}

func handleServerConnection(c net.Conn){
    //receive the message
    var msg string
    err := gob.NewDecoder(c).Decode(&msg)
    if err != nil{
        fmt.Println(err)
    }else{
        fmt.Println("Received", msg)
    }
    c.Close()
}

func client(){
    //connect to the server
    c, err := net.Dial("tcp", "127.0.0.1:8080")
    if err != nil{
        fmt.println(err)
        return
    }

    //server the message 
    msg := "Hello, World"
    fmt.Println("Sending", msg)
    err = gob.newEncoder(c).Encode(msg)
    if err != nil{
        fmt.println(err)
    }
    c.Close()
}

func main(){
    go server()
    go client()

    var input string
    fmt.Scanln(&input)
}
```

Here in this program, we are using some of the packages which are used to perform certain functions like

* the "`encoding/gob`" package which makes it easy to encode GO values so that other Go programs can read them. Additional encoding is possible in packages underneath encoding as well as in third-party packages.
    
* "`net`" is already been described with its listener function above.
    
* "`fmt`" function is sued for general purpose use which reduces the chance of having overlapping names, organizes our code so that it's easier to find code to edit, and speeds up the compiler by only requiring recompilation of smaller chunks of a program.
    
* In the provided code snippet, `ln` and `err` are used in the `server()` function for error handling and to establish a TCP listener on a specific port. The `net.Listen()` function is used to create a TCP listener that listens for incoming connections on a specified network address. In this case, it listens on TCP network address "8080". The function returns a `net.Listener` object (`ln`) and an error (`err`) if any occurred during the listener creation.
    
* The `ln.Accept()` function in the for loop is called to accept an incoming client connection. It waits until a client connects to the listener (`ln`) and returns a `net.Conn` object (`c`) representing the connection and an error (`err`) if any occurred during the acceptance process.
    
* `gob.NewDecoder` and `gob.NewEncoder` is used for serialization and deserialization of messages between the server and the client. The `gob` package provides functionality for encoding and decoding Go values in a compact binary format. `gob.NewDecoder` is used in the coed to decode the message accepted from the client connection and then `gob.NewEncoder`is used to deserialize the message into the binary form msg which is in the string format and variable in nature as defined in the `handleServerConnection` function.
    

## HTTP

HTTP(Hyper Text Transfer Protocol) servers are even easier to set up and use:

```go
package main

import ("net/http" ; "io")

func hello(res http.ResponseWriter, req *http.Request){
    res.Header().Set(
        "Content-Type",
        "text/html",
    )
    io.WriteString(
        res,
        "<DOCTYPE html>
        <html>
        <head>
            <title>Hello World</title>
        </head>
        <body>
            Hello, World
        </body>
        </html>"
    )
}

func main(){
        http.HandleFunc("/hello", hello)
        http.ListenAndServer(":9000", nil)
}
```

`HandleFunc` handles a URL route (/hello) by calling the given function. We can also handle static files by using `FileServer`:

```go
http.Handle(
    "/assets/",
    http.Stripeprefix(
        "/assets/",
        http.FileServer(http.Dir("assets")),
    ),
)
```

Again here, there are a lot of sets and apckages being used in the code representing different functionality of the program as:

* `req *http.Request` is used as a parameter in the `hello` function to represent the incoming HTTP request. The `http.Request` type provides access to various information about the client's request, such as headers, URL parameters, and request body.
    
* `res.Header()` is used to access the HTTP response headers, specifically the headers of the `http.ResponseWriter` object. The `Header()` method returns an `http.Header` object, which represents the collection of headers associated with the response.
    
* `res.Header().Set("Content-Type", "text/html")` sets the `Content-Type` header of the response to `"text/html"`. The `Content-Type` header specifies the type of content being returned by the server. In this case, it indicates that the response will be in HTML format.
    
* The `io.WriteString(res, ...)` function is used to write a string response to the client. It takes the `http.ResponseWriter` object (`res`) and the string content to be written as its arguments.
    

Then the FileServer which we used to handle static files also have certain keywords and functions for different uses:

* `http.Handle` is used to associate the `/assets/` URL path with an HTTP handler. The HTTP handler being used is `http.StripPrefix`, which removes the `/assets/` prefix from the URL path before serving the static files.
    
* By combining `http.StripPrefix` and `http.FileServer` in this manner, you create a handler that serves static files from the "assets" directory, but removes the `/assets/` prefix from the URL path when looking for the corresponding file.
    
* `http.Dir("assets")` function call creates an `http.Dir` object, which represents a directory on the file system. In this case, it specifies the directory named "assets" from which the static files will be served.
    
* `http.FileServer(http.Dir("assets"))`: The `http.FileServer` function creates an HTTP handler that serves static files from the provided directory. It takes an `http.Dir` object as an argument to specify the directory containing the static files.
    

## RPC

The net/rpc (remote procedure call) and net/rpc/jsonrpc packages provide an easy way to expose methods so they can be invoked over a network rather than just running in the program.

```go
package main

import (
    "fmt"
    "net"
    "net/rpc"
)

type Server struct{}
func (this *Server) Negate(i int64, reply *int64) error{
    *reply = -i
    return nil
}

func server(){
    rpc.Register(new(Server))
    ln, err := net.Listen("tcp", ":8080")
    if err != nil{
        fmt.Println(err)
        return
    }

    for{
        c, err := ln.Accept()
        if err != nil{
            continue
        }   
        go rpc.ServerConn(c)
    }
}

func client(){
    c, err := rpc.Dial("tcp", "127.0.0.1:8080")  
    if err != nil{
        fmt.Println(err)
        return
}
  var result int64
  err = c.Call("Server.Negate", int64(999), &result)
  if err != nil{
    fmt.Println(err)
  } else {
    fmt.Println("Server.Neagte(999)=", result)
  }    
}

func main(){
    go server()
    go client()
    var input string
    fmt.Scanln(&input)
}
```

In this section there are a lot of things and functions being used in some different way than the normal format which proves to be executing the main function for which many developers use Golang which were mentioned at the beginning of the blog which are concurrency and multithreading:

* At the start of the `main` function `go server()`& `go client()` are used as, go instructs the function to use those functions concurrently as goroutine.
    
    Goroutines are lightweight concurrent threads of execution that can run concurrently with other goroutines, allowing for concurrent and parallel execution. By launching both the server and client functions as goroutines, the `main` function can continue its execution without being blocked by the server or client operations. This way, the server and client can operate concurrently and independently.
    
* The subsequent `fmt.Scanln(&input)` statement is used to keep the main function from exiting immediately. It waits for user input from the console, allowing the server and client goroutines to continue running until user input is provided.
    

Now in the general code after making a call of the different functions in the main function.

* The purpose of the `Negate` method is to allow remote procedure calls (RPC) to the server. When the client makes an RPC call to the `Negate` method on the server, passing an integer value as the argument, the server will negate the value and store the result in the `reply` parameter. The modified `reply` value is then returned to the client.
    
* `rpc.Register(new(Server))` registers an instance of the `Server` struct as an RPC service. It allows the methods defined on the `Server` struct (such as the `Negate` method) to be accessible for remote procedure calls.
    
    By calling `rpc.Register` with `new(Server)`, an instance of the `Server` struct is created and registered as an RPC service. This means that when a client makes an RPC call to the server, it can invoke methods on this registered instance of `Server`.
    
* In the client code, [`c.Call`](http://c.Call)`("Server.Negate", int64(999), &result)` makes an RPC call to the server's `Negate` method, passing `999` as the value to be negated. The negated value is then stored in the `result` variable on the client side.
    
* `go rpc.ServeConn(c)`:
    
    Starts an RPC server on the provided connection (`c`). It handles incoming RPC requests from the client and dispatches them to the appropriate registered service (in this case, the `Server` instance). By using `go` before `rpc.ServeConn(c)`, it runs the server method concurrently in a goroutine. This allows the server to handle multiple client connections simultaneously and ensures that the server doesn't block the main execution flow.
    
* The `rpc.ServeConn` function listens for RPC requests on the given connection (`c`) and serves them accordingly. It waits for an incoming request, determines which RPC method is being called, and invokes the appropriate method on the registered service.
    

## Parsing Command-Line Arguments

When we invoke a command on the terminal, it's possible to pass that command argument.

```go
go run myfile.go
```

We have seen this code already and myfile.go are arguments. We can also pass flags to a command as

```go
go run -v myfile.go
```

The flag package allows us to parse arguments and flags sent to our program. Here's an example for generating numbers from 1 to 100 as

```go
package main

import ("fmt"; "flag"; "math/rand")

func main(){
    //Define flags
    maxp := flag.Int("max", 100, "the max value")
    //Parse
    flag.Parse()
    //Generate a number between 0 and max
    fmt.Println(rand.Intn(*maxp))
}
```

Any additional non-flag arguments can be retrieved with a flag.Args(), which returns a \[\]string.

If you are a freshman who just started or going to start using Go more frequently then please read my other blogs as well which will surely help you a lot in the introduction of this language at least 😄

Soon, I will be publishing a blog on the use of testing in Go, Unit test, and Integration Test and how can we create and use them to make our code more productive

Hope you get to learn some from this blog for which you came here 😄

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[Aryan\_2407](https://twitter.com/Aryan_2407)