# Porting dq
## Introduction
[Here](https://github.com/qtronic/fmusdk/tree/master/fmu20/src/models/dq) we have a sample implementation of a FMU model. We aim to port it to [Nim](https://nim-lang.org).

It aims to solve the the Dahlquist test equation.

- der(x) = - k * x and x(0) = 1. 
- Analytical solution: x(t) = exp(-k*t).

The file [dq.c](https://github.com/qtronic/fmusdk/blob/master/fmu20/src/models/dq/dq.c) goes as follows.

Define `class name` and `unique id`:
```c
#define MODEL_IDENTIFIER dq
#define MODEL_GUID "{8c4e810f-3df3-4a00-8276-176fa3c9f000}"
```





