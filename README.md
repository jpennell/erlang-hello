#Erlang "Hello World!"

See the following [blog post](http://egarson.blogspot.ca/2008/03/real-erlang-hello-world.html)

##hello1.erl

``` erlang
-module(hello1).
-export([start/0]).

start() ->
    io:format("Hello, World!~n").
```

###Executing hello1.erl

Open the erlang shell

``` shell
$ erl
Erlang R15B02 (erts-5.9.2) [source] [64-bit] [smp:8:8] [async-threads:0] [hipe] [kernel-poll:false] [dtrace]

Eshell V5.9.2  (abort with ^G)
1>
```

Compile hello1.erl -> hello1.beam

``` shell
1> c(hello1).
{ok,hello1}
```

Invoke the start() function and it should print out "Hello World!"

``` shell
2> hello1:start().
Hello, World!
ok
```

Ctrl-C + a will quit

##hello2.erl

``` erlang
-module(hello).
-export([start/0]).

start() ->
   spawn(fun() -> loop() end).

loop() ->
   receive
      hello ->
         io:format("Hello, World!~n"),
         loop();

      goodbye ->
         ok
   end.

```

###Executing hello2.erl

Open the erlang shell

``` shell
$ erl
Erlang R15B02 (erts-5.9.2) [source] [64-bit] [smp:8:8] [async-threads:0] [hipe] [kernel-poll:false] [dtrace]

Eshell V5.9.2  (abort with ^G)
1>
```

Compile hello2.erl -> hello2.beam

``` shell
1> c(hello2).
{ok,hello2}
```

Invoke the start() function and assign the return value to a variable called Pid (variables in Erlang must start with an uppercase letter).
Erlang will pretty print the process identifier.

``` shell
2> Pid = hello2:start().
<0.38.0>
```

Invoke the hello clause

``` shell
3> Pid ! hello.
Hello, World!
hello
```

Invoke the goodbye clause

``` shell
4> Pid ! goodbye.
goodbye
```

Ctrl-C + a will quit
