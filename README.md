# underTheHoodOf-JS
Let's take a deep dive into how a JS Engine works 

JavaScript Works Under The Hood: An Overview of JavaScript Engine, Heap and, Call Stack

Many JavaScript developers don't know how JavaScript works under the hood. If you are new to JavaScript 👶, then this article will help to learn how JavaScript works under the hood. If you are an experienced 👴, JavaScript developer hopefully, this article will be a good refresher for you.

⚙️ JavaScript Engine
The JavaScript engine is a program that executes your JavaScript code. A popular example of a JavaScript engine is Google's V8 engine.

⚙️ V8 Engine
The V8 engine is an open-source, high-performance JavaScript and Web Assembly engine written in C++. The V8 engine is used inside Google Chrome, Node.js, and electron, among others.

Overview of V8 Engine
![pkm3gblxjo6dvxn6cs59](https://user-images.githubusercontent.com/32735357/80788313-63989f00-8ba6-11ea-89f4-cc1da7c7f4c3.png)


The V8 engine has two main components

>Heap is an unstructured memory that is used for memory allocation of the variables and the objects.

>Call Stack is a data structure that is used for function calls that record where we are in the program.
🥞 Call Stack
JavaScript is a single-threaded programming language, which means it can do one thing at a time, and it has one Call Stack.

![ksbkcvxzxokwflc2ecvt](https://user-images.githubusercontent.com/32735357/80788398-993d8800-8ba6-11ea-8d20-a01eefd7b552.png)


If you call a function, it's pushed on the top of the Call Stack, and when the function returns, it's popped from the top of the Call Stack.

Let's take an example.

                      function one() {
                        return 1;
                      }

                      function two() {
                        return one() + 1;
                      }

                      function three() {
                        return two() + 1;
                      }

                      console.log(three());

Call Stack Visualization
![v0rlrajikz1hdhduswca](https://user-images.githubusercontent.com/32735357/80788453-c7bb6300-8ba6-11ea-8577-885dc6f50f4c.gif)

Let's take another example that contains an error.


                                  function one() {
                                    // throws an error
                                    throw new Error("Oops");
                                  }

                                  function two() {
                                    return one() + 1;
                                  }

                                  function three() {
                                    return two() + 1;
                                  }

                                  console.log(three());

Call Stack Visualization

![cq37yxj9m3t6v59bysvi](https://user-images.githubusercontent.com/32735357/80788493-ed486c80-8ba6-11ea-82f1-236a5343a287.gif)

When the V8 engine encounters an error, it prints a stack trace. A stack trace is basically the state of the Call Stack.

Let's take another example that blows up the Call Stack 💥.

We can do this by using a recursive function.

                                function recursion() {
                                  recursion();
                                }

                                console.log(recursion());


Call Stack Visualization
![etevycrnjmom6vw6inwb](https://user-images.githubusercontent.com/32735357/80791781-57b1da80-8bb0-11ea-83da-cf829f963515.gif)

A recursive function calls itself again and again. At some point in time, the number of function calls exceeds the actual size of the stack, and the browser detects this to take action by throwing an error.

I hope now you have a fair understanding of how JavaScript engine works under the hood.



