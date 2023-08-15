---
title: "Bridging the gap between Concurrency and Parallelism in     Go"
seoTitle: "Bridging the gap between Concurrency and Parallelism in     Go"
seoDescription: "Wanna know about Concurrency pros/cons | Difference b/w Parallelism & Concurrency differences and ways to manage them then here it is...."
datePublished: Tue Aug 15 2023 14:07:55 GMT+0000 (Coordinated Universal Time)
cuid: cllcdp3iq000709l9fg573fwa
slug: bridging-the-gap-between-concurrency-and-parallelism-in-go
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692005624749/390d779c-1452-44ef-a63a-57af8134f39c.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692107157544/9f499365-a787-42d4-8312-9f49de2a038f.jpeg
tags: go, concurrency, google, technical-writing-1, wemakedevs

---

One of the main features of Go is Concurrency and its modeling to manage problems caused by concurrency in any particular language, which might have made a lot of programmers and machine learning students a bit irritated when I considered concurrency problematic. If you do know about those problems then you can skip to the main part but, if you are a beginner or don't know about these cons of concurrency then here we go:--

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106169271/443fd68d-ce94-4bbf-aaf5-41607b0364c8.png align="center")

# What is Concurrency?

Concurrency allows us to run several functions and processes at one time without waiting for the previous one to get completed. Here it sets out our foot at a much more efficient and consistent step to use multi-core processes much more efficiently, but it's also the reason which causes a lot of trouble for developers due to the management of the time when the desired and the required function will get executed in code.

Concurrent code is difficult and takes up a pretty good effort to make the code work as expected this start giving errors and shows up some undiscovered bugs to head up which weren't visible for a long time and upfronted due to some change in time, eventually causes a lot of trouble for computer scientists. now we will be discussing some of the issues which build up this complexity and irritation while using concurrency in code.

## Race Conditions

A race condition occurs when two programs must execute at the correct time, but the program has not been written so that the order is guaranteed to be maintained.

When one concurrent function attempts to read a variable while at some undetermined time, another concurrent operation is attempting to write to the same variable then this breaks out to what is known as a *data race*.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106612584/9fd16cb1-d0dc-4c4d-a308-5e1ca0c16aa3.jpeg align="center")

The main reason behind this data race is that most of the time developers are thinking the program will get executed sequentially, they assume that the program they written will get executed line by line as they mentioned in the code. When writing code, you have to meticulously iterate through the possible scenarios.

```go
var data int 
go fun() {data++}()
time.Sleep(3*time.Second)
if data == 0 {
    fmt.Printf("Concurrency is cool")
}
```

Most of the developers, who do know something about the language and its use cases, might consider sprinkling sleep in your code to jump off the chances of falling into the race conditions as people might think the longer we sleep in between invoking our goroutines and checking the value of data, the closer our program get to achieving correctness. This condition might seem to be working firsthand in some cases even for some complex conditions but it will not always flow so frictionlessly and will bump out to pointing errors at some time due to eth execution of wrong functions at the wrong time.

In addition, we have also introduced an inefficiency after introducing sleep in our code.

Race conditions are one of the most insidious types of concurrency bugs because they may not show up until years after the code has been placed into production. They are usually precipitated by a change in the environment the code is executing in, or an unprecedented occurrence. In these cases, the code seems to be behaving correctly, but in reality, there's just a high chance that the operations will be executed in order. Sooner, or later, the program will have unintended consequences.

## Atomicity

The first thing that comes to mind when we hear atomicity is dependent on the size of something relatively smaller than the environment we are referring to, as something atomic in nature is atomic or smaller than the environment we are referring to but it might not be atomic to the objects similar its size in surroundings.

Similarly, in computer science we often talk about atomicity with the example of, Operations that are atomic within the context of the operating system but may not be atomic within the context of your machine, and operations that are atomic in the context of a computer machine may not be atomic in context of your application. In other words, the atomicity of an operation can change depending on the currently defined scope.

When thinking about atomicity, very often the first thing you need to do is define the context or scope, the operation will be considered to be atomic.

"Indivisible" or "Uninterruptible" means that within the context you have defined, something that is atomic will happen in its entirety without anything happening in that context simultaneously.

## Memory Access Synchronization

in concurrent functions, we might experience problems in which the same area of memory is attempted to get accessed by two different concurrent functions. This section of code that needs exclusive access to a shared resource is known as the *critical section*. One way to solve this problem is to synchronize your access to the memory between your critical sections. Let's take a beginner-level problem to grab a better understanding of this concept.

```go
var memoryAccess sync.Mutex
var value int 
gop func(){
    memoryAccess.lock()
    value++
    memory.Access.Unlock()
}()

memoryAccess.Lock()
if value == 0{
    fmt.Printf("the value is %v. \n", value)
}else{
    fmt.Printf("the value is %v.\n", value)
}
memory.Access.Unlock()
```

* `var memoryAccess sync.Mutex` - Here, we added a variable that will allow our code to synchronize access to the data variable's memory.
    
* `memoryAccess.Lock()` - Here, we declared that until we declare otherwise, our goroutine should have exclusive access to the memory.
    
* `memoryAccess.Unlock()`\- Here we declared that the goroutine is done with this memory.
    

**Anytime developers, felt to access the data variable's memeory they must first call the Lock, and when they are finished accessing the variable's memmory and managing and manipulating the tasks they must call Unlock. Code between these two statements can then assume to contain exclusive access to data, we have successfully synchronized access to the memory**.

By this example, we might have succeeded in narrowing the scope of non-determinism a bit but we haven't really solved our whole problem by this, because we have seen it doesn't solve the data races automatically or might have solved logical races on its own also it may result in maintenance and performance problems.

Synchronizing access to the memory in this way also has performance ramifications. There are some other technical issues as well which if didn't handle properly can even stop the functioning of the whole code altogether.

## Deadlocks

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106848693/d09bf7dd-6e4b-4159-8b82-175f41faca7d.jpeg align="center")

A deadlock program is one in which all concurrent processes are waiting on one another. In this case, the code will never recover without outer intervention. The Go runtime will attempt to do some parts on its own and detect some deadlocks, but this won't do much to help to prevent deadlocks.

```go
type value struct{
    mu sync.Mutex
}
    value int
}

var wg sync.WaitGroup
printSum := func(v1, v2*value){
    defer wg.Done()
    v1.mu.Lock()
    defer v1.mu.Unlock()
    
    time.Sleep(2*time.Second)
    v2.mu.Lock()
    defer v1.mu.Unlock()

    fmt.Printf("sum = %v\n", v1.value + v2.value)
}

var a, b value
wg.Add(2)
go printSum(&a, &b)
go printSum(&b, &a)
wg.Wait()
```

Here as described in the previous example as well we have used synchronization By Lock and Unlock to access our memory but in this code, we have also used defer in the Unlock part to exit section before printSum returns.

Here in this code, we will get an error due to the deadlocks in it which occurred due to a timing issue in this code in the written code, we can see that the printSum statement has locked a and then attempts to lock b but right in the next line of the code we have seen the printSum function has locked b and attempts to lock a.

## Livelock

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106870885/978025fc-2178-46d4-aeae-a19c13b64c63.jpeg align="center")

Livelocks are programs that are actively performing concurrent operations, but these operations do nothing to move the state of the program forward. Let's try to understand them by an example:

```go
toss := func(tossing *sync.WaitGroup, name string){
  var out bytes.Buffer  
  defer func() {fmt.Println(out.String())}  
  defer tossing.Done()  
  fmt.Fprintf("&out, %v is trying to call a toss", name)    
  for i := 0; i < 5; i++{  
    if tryHeads(&out) || tryTails(&out)          
        return 
    }
}
    fmt.Fprintf(&out, "\n%v got a chance", name)
} 

var peopleInHallway sunc.Waitgroup
peopleInHallway.Add(2)
go toss(&peopleInHallway, "India")
go toss(&peopleInHallway, "Australia")
peopleInHallway.Wait()
```

Here is an example of livelocks where a certain condition and a limit have been implemented to stop the execution of the code up to a certain point to restrict it from running forever.

The function will try to attempt Heads and if that fails then it will attempt to try Tails. The variable will wait until one of them either gives up or wins.

Here, if we try to run the code then it won't reach out to any endpoint and would give heads and tails continuously in each case.

Livelocks are even more difficult than deadlocks and bring up a kind of an illusion of the users which looks as if the program is executing and creating some results, even if the limits have been set in this condition then also there is a bit of a chance that the condition set didn't give the correct results. Even to recheck if you would think of reviewing the CPU utilization, you will get to know that the CPU is being utilized at the moment, which would push you to think it was doing work.

## Starvation

Starvation is any situation where a concurrent process cannot get all the resources it needs to perform work. Starvation usually implies that they are some greedy functions running concurrently which prevents other concurrent functions to work efficiently.

```go
var wg sync.WaitGroup
var sharedLock sync.Mutex
const runtime = 1*time.Second

greedyWorker := func() {
     defer wg.Done()

     var count int
     for begin := time.Now(); time.Since(begin) <= runtime; {
         sharedLock.Lock()
         time.Sleep(3*time.Nanosecond)
         sharedLock.Unlock()
         count++
     }
 fmt.Printf("Greedy worker was able to execute %v work loops\n", count)
}

politeWorker := func() {
     defer wg.Done()
 
    var count int
     for begin := time.Now(); time.Since(begin) <= runtime; {
         sharedLock.Lock()
         time.Sleep(1*time.Nanosecond)
         sharedLock.Unlock()

         sharedLock.Lock()
         time.Sleep(1*time.Nanosecond)
         sharedLock.Unlock()

         sharedLock.Lock()
         time.Sleep(1*time.Nanosecond)
         sharedLock.Unlock()

         count++
 }

    fmt.Printf("Polite worker was able to execute %v work loops.\n", count)
}
wg.Add(2)
go greedyWorker()
go politeWorker()
wg.Wait()
```

If we run this code we would see the following output

```go
Polite worker was able to execute 289777 work loops.
Greedy worker was able to execute 471287 work loops
```

If we would take it as both the functions have same-size critical sections, rather than concluding that the greedy worker's algorithm is more efficient then we have concluded that the greedy worker has unnecessarily expanded its hold on the shared lock beyond its critical section and is preventing the polite function from performing its own work.

For solving the problem of starvation we often use- `metric`. Starvation makes up for a good argument for recording and sampling metrics. One of the ways you can detect and solve starvation is by logging when work is aggregated and then determining if your rate is as high as you expect from it or not. Starvation can also apply to CPU, memory, file handles, database connections or any resource that must be shared is a candidate for starvation.

# Concurrency v/s Parallelism

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106919426/23858c32-2355-4113-9a85-6ee5d275e935.jpeg align="center")

Many people often confuse these two words and tend to use both of them together without giving a second thought to trying to understand who stands on which terrain and which is more useful at which condition specifically.

***Concurrency is different from Parallelism***

Concurrency is a situation in which more than one function or multiple functions run and execute together, whose problems and benefits we have seen in the previous paragraphs and lines( if you have skipped to this part and know about the advantages but don't know much about the disadvantages then please head back to those interesting topics).

You might see the following line to be printed everywhere in every book which talks about the difference between concurrency and parallelism:-

***Concurrency is a property of code while parallelism is a property of a running program.***

The chunks of our program may appear to be running in parallel, but really they are executing in a sequential manner faster than is distinguishable. The CPU context switches to share time between programs, and over a coarse enough granularity of time, the tasks appear to be running in parallel. We do not write parallel code, only concurrent code that we hope will run in parallel. Parallelism is a property of the runtime of our program, not the code.

This is only made possible by the layers of abstraction that lie beneath our program’s model: the concurrency primitives, the program’s runtime, the operating system, and the platform the operating system runs on the CPUs.

It may not do us much good to go about redefining our context in terms of time slices but remember context isn’t constrained to time. We can define a context as the process our program runs within, its operating system thread, or its machine. This is important because the context you define is closely related to the concept of concurrency and correctness.

Due to the rising importance of modeling our concurrent code, our abstractions are becoming more and more important to us. In other words, the more difficult it is to get concurrency right, the more important it is to have access to concurrency primitives that are easy to compose.

Most concurrent logic in our industry is written at one of the highest levels of abstraction- ***OS threads***. Before Go was first revealed to the public, this was where the chain of abstraction ended for most of the popular programming languages. If you wanted to write concurrent code, you would model your program in terms of ***threads*** and synchronize the access to the memory between them. If you had a lot of things you had to model concurrently and your machine couldn’t handle that many threads, you created a ***thread pool*** and multiplexed your operations onto the thread pool.

Since we haven't added any additional level of abstraction on top of OS threads, we would observe that adding new abstractions below OS threads would make things easier than before and we would barely have to think about our threads anymore instead we will be modeling things in terms of goroutines, channels and even, shared memories in between the code at required places.

## Diving a bit deeper...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106979222/0f9e4739-d490-49d9-9b71-a257a9b4f393.jpeg align="center")

If we were to draw a comparison between concepts in the two ways of abstracting concurrent code, we’d probably compare the goroutine to a thread, and a channel to a mutex.

Goroutines free us from having to think about our problem space in terms of parallelism and instead allow us to model problems closer to their natural level of concurrency.

If you were to build a web server that fields requests on an endpoint. If we step back and think about the natural problem, individual users are connecting to my endpoint and opening a session. The session should field their request and return a response. In Go, we can almost directly represent the natural state of this problem in code and create a goroutine for each incoming connection, field the request there, and then return from the goroutine’s function.

Goroutines are lightweight, and we normally won’t have to worry about creating one. There are appropriate times to consider how many goroutines are running in your system, but doing so upfront is soundly a premature optimization.

Thread has a framework available for a language that abstracts the concerns of parallelism away from you. Go was designed around concurrency, so the language is not incongruent with the concurrency primitives it provides, with less friction and fewer bugs! A more natural mapping of the problem space is an enormous benefit, but it has a few beneficial side effects as well.

Go’s runtime multiplexes goroutines onto OS threads automatically and manages their scheduling for us. This means that optimizations to the runtime can be made without us having to change how we’ve modeled our problem.

This decoupling of concurrency and parallelism has another benefit: because Go’s runtime is managing the scheduling of goroutines for you, it can introspect on things like goroutines blocked waiting for Input/Output and intelligently reallocate OS threads to goroutines that are not blocked. This also increases the performance of your code, also benefit of the more natural mapping between problem spaces and Go code is the likely increased amount of the problem space modeled concurrently.

Channels, for instance, are inherently composable with other channels. This makes writing large systems simpler because you can coordinate the input from multiple subsystems by easily composing the output together.

The select statement is the complement to Go’s channels and is what enables all the difficult bits of composing channels. select statements to allow you to efficiently wait for events, select a message from competing channels in a uniform random way, continue on if no messages are waiting, and more.

Package sync provides basic synchronization primitives such as mutual exclusion locks. Other than the Once and WaitGroup types, most are intended for use by low-level library routines. Higher-level synchronization is better done via channels and communication.

***Do not communicate by sharing memory. Instead, share memory by communicating.***

Some other patterns and practices are useful in languages that use the OS thread as the means of abstracting concurrency. For example, things like thread pools often come up. Because most of these abstractions are targeted toward the strengths and weaknesses of OS threads, a good rule when working with Go is to discard these patterns. That’s not to say they aren’t useful at all, but the use cases are certainly much more constrained in Go. Stick to modeling your problem space with goroutines, use them to represent the concurrent parts of your workflow, and don’t be afraid to be liberal when starting them. You’re much more likely to need to restructure your program than you are to begin running into the upper limit of how many goroutines your hardware can support.

Go’s philosophy on concurrency can be summed up like this:

***Aim for simplicity, use channels when possible, and treat goroutines like a free resource.***

Hope you get to learn some from this blog for which you came here 😄. Soon I will be releasing other blogs explaining about Go Building blocks- Threads, Goroutines, channels, OS Threads and a lot more, & will get our hands a bit more dirty with em 🔥🔥.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692106044263/837bd4e4-e191-42dd-96a0-e382e79d868a.gif align="center")

If you like my Article then please react to it and connect with me on Twitter if you are also a tech enthusiast. I would love to collaborate with people and share the experience of tech😄😄.

My Twitter Profile:

[Aryan\_2407](https://twitter.com/Aryan_2407)