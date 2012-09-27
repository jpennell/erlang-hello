Erlang Hello World
============

See the following [blog post](http://egarson.blogspot.ca/2008/03/real-erlang-hello-world.html)

Example of running hello.erl


Open the erlang shell

``` shell
$ erl
Erlang R15B02 (erts-5.9.2) [source] [64-bit] [smp:8:8] [async-threads:0] [hipe] [kernel-poll:false] [dtrace]

Eshell V5.9.2  (abort with ^G)
1>
```

Compile hello.erl -> hello.beam

``` shell
1> c(hello).
{ok,hello}
```

Invoke the start() function and assign the return value to a variable called Pid (variables in Erlang must start with an uppercase letter).
Erlang will pretty print the process identifier.

``` shell
2> Pid = hello:start().
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
