# Porting dq
## Introduction
[Here](https://github.com/qtronic/fmusdk/tree/master/fmu20/src/models/dq) we have a sample implementation of a FMU model. We aim to port it to [Nim](https://nim-lang.org).

It aims to solve the the Dahlquist test equation.

- der(x) = - k * x and x(0) = 1. 
- Analytical solution: x(t) = exp(-k*t).

# Analysis
## The C-code
The file [dq.c](https://github.com/qtronic/fmusdk/blob/master/fmu20/src/models/dq/dq.c) goes as follows.

Define **class name** and **unique id**:
```c
#define MODEL_IDENTIFIER dq
#define MODEL_GUID "{8c4e810f-3df3-4a00-8276-176fa3c9f000}"
```
!!! note
    **MODEL_IDENTIFIER**  is used by macros in order to create new function names. So it renames: **fmiWhatever** into **dq_fmiWhatever**

Then it defines the model size:
```c
#define NUMBER_OF_REALS 3
#define NUMBER_OF_INTEGERS 0
#define NUMBER_OF_BOOLEANS 0
#define NUMBER_OF_STRINGS 0
#define NUMBER_OF_STATES 1
#define NUMBER_OF_EVENT_INDICATORS 0
```

!!! note
    This values need to be aligned with the .xml file describing the model.

Then:
```c
// include fmu header files, typedefs and macros
#include "fmuTemplate.h"
```

Then:
```c
// define all model variables and their value references
// conventions used here:
// - if x is a variable, then macro x_ is its variable reference
// - the vr of a variable is its index in array  r, i, b or s
// - if k is the vr of a real state, then k+1 is the vr of its derivative
#define x_     0
#define der_x_ 1
#define k_     2
```

Then:
```c
// define state vector as vector of value references
#define STATES { x_ }
```

Then:
```c
// called by fmi2Instantiate
// Set values for all variables that define a start value
// Settings used unless changed by fmi2SetX before fmi2EnterInitializationMode
void setStartValues(ModelInstance *comp) {
    r(x_) = 1;
    r(k_) = 1;
}
```

Then:
```c
// called by fmi2GetReal, fmi2GetInteger, fmi2GetBoolean, fmi2GetString, fmi2ExitInitialization
// if setStartValues or environment set new values through fmi2SetXXX.
// Lazy set values for all variable that are computed from other variables.
void calculateValues(ModelInstance *comp) {
    //if (comp->state == modelInitializationMode) {
    //  initialization code here
    //  set first time event, if any, using comp->eventInfo.nextEventTime
    //}
}
```

Then:
```c
// called by fmi2GetReal, fmi2GetContinuousStates and fmi2GetDerivatives
fmi2Real getReal(ModelInstance* comp, fmi2ValueReference vr){
    switch (vr) {
        case x_     : return r(x_);
        case der_x_ : return - r(k_) * r(x_);
        case k_     : return r(k_);
        default: return 0;
    }
}
```

Then:
```c
// used to set the next time event, if any.
void eventUpdate(ModelInstance *comp, fmi2EventInfo *eventInfo, int isTimeEvent, int isNewEventIteration) {
} 
```

Then:
```c
// include code that implements the FMI based on the above definitions
#include "fmuTemplate.c"
```