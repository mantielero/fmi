# fmuTemplate.h
## Wrapper en Nim
Tendrá la siguiente pinta:
```nim

{.passC: "-DDISABLE_PREFIX".}


{.passC: "-I/home/jose/src/nimlang/fmusdk-master/fmu20/src/shared/include".}

{.passC: "-I/home/jose/src/nimlang/fmusdk-master/fmu20/src/shared".}
# Importing /home/jose/src/nimlang/fmusdk-master/fmu20/src/models/fmuTemplate.h
# Generated at 2019-10-17T23:02:05+02:00
# Command line:
#   /home/jose/.nimble/pkgs/nimterop-#head/nimterop/toast --preprocess --recurse --defines+=DISABLE_PREFIX --includeDirs+=/home/jose/src/nimlang/fmusdk-master/fmu20/src/shared/include --includeDirs+=/home/jose/src/nimlang/fmusdk-master/fmu20/src/shared --pnim --nim:/home/jose/.choosenim/toolchains/nim-1.0.0/bin/nim /home/jose/src/nimlang/fmusdk-master/fmu20/src/models/fmuTemplate.h

{.hint[ConvFromXtoItselfNotNeeded]: off.}

import nimterop/types



#  This header file must be utilized when compiling an FMU or an FMI master.
#    It declares data and function types for FMI 2.0
#    Revisions:
#    - Apr.  9, 2014: all prefixes "fmi" renamed to "fmi2" (decision from April 8)
#    - Apr.  3, 2014: Added #include <stddef.h> for size_t definition
#    - Mar. 27, 2014: Added #include "fmiTypesPlatform.h" (#179)
#    - Mar. 26, 2014: Introduced function argument "void" for the functions (#171)
#                       fmiGetTypesPlatformTYPE and fmiGetVersionTYPE
#    - Oct. 11, 2013: Functions of ModelExchange and CoSimulation merged:
#                       fmiInstantiateModelTYPE , fmiInstantiateSlaveTYPE  -> fmiInstantiateTYPE
#                       fmiFreeModelInstanceTYPE, fmiFreeSlaveInstanceTYPE -> fmiFreeInstanceTYPE
#                       fmiEnterModelInitializationModeTYPE, fmiEnterSlaveInitializationModeTYPE -> fmiEnterInitializationModeTYPE
#                       fmiExitModelInitializationModeTYPE , fmiExitSlaveInitializationModeTYPE  -> fmiExitInitializationModeTYPE
#                       fmiTerminateModelTYPE , fmiTerminateSlaveTYPE  -> fmiTerminate
#                       fmiResetSlave -> fmiReset (now also for ModelExchange and not only for CoSimulation)
#                     Functions renamed
#                       fmiUpdateDiscreteStatesTYPE -> fmiNewDiscreteStatesTYPE
#                     Renamed elements of the enumeration fmiEventInfo
#                       upcomingTimeEvent             -> nextEventTimeDefined  due to generic naming scheme: varDefined + var
#                       newUpdateDiscreteStatesNeeded -> newDiscreteStatesNeeded;
#    - June 13, 2013: Changed type fmiEventInfo
#                     Functions removed:
#                        fmiInitializeModelTYPE
#                        fmiEventUpdateTYPE
#                        fmiCompletedEventIterationTYPE
#                        fmiInitializeSlaveTYPE
#                     Functions added:
#                        fmiEnterModelInitializationModeTYPE
#                        fmiExitModelInitializationModeTYPE
#                        fmiEnterEventModeTYPE
#                        fmiUpdateDiscreteStatesTYPE
#                        fmiEnterContinuousTimeModeTYPE
#                        fmiEnterSlaveInitializationModeTYPE;
#                        fmiExitSlaveInitializationModeTYPE;
#    - Feb. 17, 2013: Added third argument to fmiCompletedIntegratorStepTYPE
#                     Changed function name "fmiTerminateType" to "fmiTerminateModelType" (due to #113)
#                     Changed function name "fmiGetNominalContinuousStateTYPE" to
#                                           "fmiGetNominalsOfContinuousStatesTYPE"
#                     Removed fmiGetStateValueReferencesTYPE.
#    - Nov. 14, 2011: First public Version
#    Copyright � 2011 MODELISAR consortium,
#                2012-2013 Modelica Association Project "FMI"
#                All rights reserved.
#    This file is licensed by the copyright holders under the BSD 2-Clause License
#    (http:www.opensource.org/licenses/bsd-license.html):
#    ----------------------------------------------------------------------------
#    Redistribution and use in source and binary forms, with or without
#    modification, are permitted provided that the following conditions are met:
#    - Redistributions of source code must retain the above copyright notice,
#      this list of conditions and the following disclaimer.
#    - Redistributions in binary form must reproduce the above copyright notice,
#      this list of conditions and the following disclaimer in the documentation
#      and/or other materials provided with the distribution.
#    - Neither the name of the copyright holders nor the names of its
#      contributors may be used to endorse or promote products derived
#      from this software without specific prior written permission.
#    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#    "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED
#    TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
#    PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
#    CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
#    EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
#    PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
#    OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
#    WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
#    OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
#    ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#    ----------------------------------------------------------------------------
#    with the extension:
#    You may distribute or publicly perform any modification only under the
#    terms of this license.
#    (Note, this means that if you distribute a modified file,
#     the modified file must also be provided under this license).
# 
#  make sure all compiler use the same alignment policies for structures
#  Include stddef.h, in order that size_t etc. is defined
#  Type definitions
defineEnum(fmi2Status)
defineEnum(fmi2Type)
defineEnum(fmi2StatusKind)
defineEnum(ModelState)

const
  headerfmuTemplate {.used.} = "/home/jose/src/nimlang/fmusdk-master/fmu20/src/models/fmuTemplate.h"

#  Values for fmi2Boolean
  fmi2True* = 1
  fmi2False* = 0
  fmi2OK* = 0.fmi2Status
  fmi2Warning* = 1.fmi2Status
  fmi2Discard* = 2.fmi2Status
  fmi2Error* = 3.fmi2Status
  fmi2Fatal* = 4.fmi2Status
  fmi2Pending* = 5.fmi2Status
  fmi2ModelExchange* = 0.fmi2Type
  fmi2CoSimulation* = 1.fmi2Type
  fmi2DoStepStatus* = 0.fmi2StatusKind
  fmi2PendingStatus* = 1.fmi2StatusKind
  fmi2LastSuccessfulTime* = 2.fmi2StatusKind
  fmi2Terminated* = 3.fmi2StatusKind

#  categories of logging supported by model.
#  Value is the index in logCategories of a ModelInstance.
  LOG_ALL* = 0
  LOG_ERROR* = 1
  LOG_FMI_CALL* = 2
  LOG_EVENT* = 3
  NUMBER_OF_CATEGORIES* = 4
  modelStartAndEnd* = (1 shl 0).ModelState
  modelInstantiated* = (1 shl 1).ModelState
  modelInitializationMode* = (1 shl 2).ModelState
  modelEventMode* = (1 shl 3).ModelState
  modelContinuousTimeMode* = (1 shl 4).ModelState
  modelStepComplete* = (1 shl 5).ModelState
  modelStepInProgress* = (1 shl 6).ModelState
  modelStepFailed* = (1 shl 7).ModelState
  modelStepCanceled* = (1 shl 8).ModelState
  modelTerminated* = (1 shl 9).ModelState
  modelError* = (1 shl 10).ModelState
  modelFatal* = (1 shl 11).ModelState

{.pragma: impfmuTemplate, importc, header: headerfmuTemplate.}
{.pragma: impfmuTemplateC, impfmuTemplate, cdecl.}

type

#  ---------------------------------------------------------------------------*
#  * fmuTemplate.h
#  * Definitions by the includer of this file
#  * Copyright QTronic GmbH. All rights reserved.
#  * ---------------------------------------------------------------------------
#  C-code FMUs have functions names prefixed with MODEL_IDENTIFIER_.
#  Define DISABLE_PREFIX to build a binary FMU.
#  This header file must be utilized when compiling a FMU.
#    It defines all functions of the
#          FMI 2.0 Model Exchange and Co-Simulation Interface.
#    In order to have unique function names even if several FMUs
#    are compiled together (e.g. for embedded systems), every "real" function name
#    is constructed by prepending the function name by "FMI2_FUNCTION_PREFIX".
#    Therefore, the typical usage is:
#       #define FMI2_FUNCTION_PREFIX MyModel_
#       #include "fmi2Functions.h"
#    As a result, a function that is defined as "fmi2GetDerivatives" in this header file,
#    is actually getting the name "MyModel_fmi2GetDerivatives".
#    This only holds if the FMU is shipped in C source code, or is compiled in a
#    static link library. For FMUs compiled in a DLL/sharedObject, the "actual" function
#    names are used and "FMI2_FUNCTION_PREFIX" must not be defined.
#    Revisions:
#    - Apr.  9, 2014: all prefixes "fmi" renamed to "fmi2" (decision from April 8)
#    - Mar. 26, 2014: FMI_Export set to empty value if FMI_Export and FMI_FUNCTION_PREFIX
#                     are not defined (#173)
#    - Oct. 11, 2013: Functions of ModelExchange and CoSimulation merged:
#                       fmiInstantiateModel , fmiInstantiateSlave  -> fmiInstantiate
#                       fmiFreeModelInstance, fmiFreeSlaveInstance -> fmiFreeInstance
#                       fmiEnterModelInitializationMode, fmiEnterSlaveInitializationMode -> fmiEnterInitializationMode
#                       fmiExitModelInitializationMode , fmiExitSlaveInitializationMode  -> fmiExitInitializationMode
#                       fmiTerminateModel, fmiTerminateSlave  -> fmiTerminate
#                       fmiResetSlave -> fmiReset (now also for ModelExchange and not only for CoSimulation)
#                     Functions renamed:
#                       fmiUpdateDiscreteStates -> fmiNewDiscreteStates
#    - June 13, 2013: Functions removed:
#                        fmiInitializeModel
#                        fmiEventUpdate
#                        fmiCompletedEventIteration
#                        fmiInitializeSlave
#                     Functions added:
#                        fmiEnterModelInitializationMode
#                        fmiExitModelInitializationMode
#                        fmiEnterEventMode
#                        fmiUpdateDiscreteStates
#                        fmiEnterContinuousTimeMode
#                        fmiEnterSlaveInitializationMode;
#                        fmiExitSlaveInitializationMode;
#    - Feb. 17, 2013: Portability improvements:
#                        o DllExport changed to FMI_Export
#                        o FUNCTION_PREFIX changed to FMI_FUNCTION_PREFIX
#                        o Allow undefined FMI_FUNCTION_PREFIX (meaning no prefix is used)
#                     Changed function name "fmiTerminate" to "fmiTerminateModel" (due to #113)
#                     Changed function name "fmiGetNominalContinuousState" to
#                                           "fmiGetNominalsOfContinuousStates"
#                     Removed fmiGetStateValueReferences.
#    - Nov. 14, 2011: Adapted to FMI 2.0:
#                        o Split into two files (fmiFunctions.h, fmiTypes.h) in order
#                          that code that dynamically loads an FMU can directly
#                          utilize the header files).
#                        o Added C++ encapsulation of C-part, in order that the header
#                          file can be directly utilized in C++ code.
#                        o fmiCallbackFunctions is passed as pointer to fmiInstantiateXXX
#                        o stepFinished within fmiCallbackFunctions has as first
#                          argument "fmiComponentEnvironment" and not "fmiComponent".
#                        o New functions to get and set the complete FMU state
#                          and to compute partial derivatives.
#    - Nov.  4, 2010: Adapted to specification text:
#                        o fmiGetModelTypesPlatform renamed to fmiGetTypesPlatform
#                        o fmiInstantiateSlave: Argument GUID     replaced by fmuGUID
#                                               Argument mimetype replaced by mimeType
#                        o tabs replaced by spaces
#    - Oct. 16, 2010: Functions for FMI for Co-simulation added
#    - Jan. 20, 2010: stateValueReferencesChanged added to struct fmiEventInfo (ticket #27)
#                     (by M. Otter, DLR)
#                     Added WIN32 pragma to define the struct layout (ticket #34)
#                     (by J. Mauss, QTronic)
#    - Jan.  4, 2010: Removed argument intermediateResults from fmiInitialize
#                     Renamed macro fmiGetModelFunctionsVersion to fmiGetVersion
#                     Renamed macro fmiModelFunctionsVersion to fmiVersion
#                     Replaced fmiModel by fmiComponent in decl of fmiInstantiateModel
#                     (by J. Mauss, QTronic)
#    - Dec. 17, 2009: Changed extension "me" to "fmi" (by Martin Otter, DLR).
#    - Dez. 14, 2009: Added eventInfo to meInitialize and added
#                     meGetNominalContinuousStates (by Martin Otter, DLR)
#    - Sept. 9, 2009: Added DllExport (according to Peter Nilsson's suggestion)
#                     (by A. Junghanns, QTronic)
#    - Sept. 9, 2009: Changes according to FMI-meeting on July 21:
#                     meInquireModelTypesVersion     -> meGetModelTypesPlatform
#                     meInquireModelFunctionsVersion -> meGetModelFunctionsVersion
#                     meSetStates                    -> meSetContinuousStates
#                     meGetStates                    -> meGetContinuousStates
#                     removal of meInitializeModelClass
#                     removal of meGetTime
#                     change of arguments of meInstantiateModel
#                     change of arguments of meCompletedIntegratorStep
#                     (by Martin Otter, DLR):
#    - July 19, 2009: Added "me" as prefix to file names (by Martin Otter, DLR).
#    - March 2, 2009: Changed function definitions according to the last design
#                     meeting with additional improvements (by Martin Otter, DLR).
#    - Dec. 3 , 2008: First version by Martin Otter (DLR) and Hans Olsson (Dynasim).
#    Copyright � 2008-2011 MODELISAR consortium,
#                2012-2013 Modelica Association Project "FMI"
#                All rights reserved.
#    This file is licensed by the copyright holders under the BSD 2-Clause License
#    (http:www.opensource.org/licenses/bsd-license.html):
#    ----------------------------------------------------------------------------
#    Redistribution and use in source and binary forms, with or without
#    modification, are permitted provided that the following conditions are met:
#    - Redistributions of source code must retain the above copyright notice,
#      this list of conditions and the following disclaimer.
#    - Redistributions in binary form must reproduce the above copyright notice,
#      this list of conditions and the following disclaimer in the documentation
#      and/or other materials provided with the distribution.
#    - Neither the name of the copyright holders nor the names of its
#      contributors may be used to endorse or promote products derived
#      from this software without specific prior written permission.
#    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#    "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED
#    TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
#    PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
#    CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
#    EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
#    PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
#    OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
#    WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
#    OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
#    ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#    ----------------------------------------------------------------------------
#    with the extension:
#    You may distribute or publicly perform any modification only under the
#    terms of this license.
#    (Note, this means that if you distribute a modified file,
#     the modified file must also be provided under this license).
# 
#  Standard header file to define the argument types of the
#    functions of the Functional Mock-up Interface 2.0.
#    This header file must be utilized both by the model and
#    by the simulation engine.
#    Revisions:
#    - Apr.  9, 2014: all prefixes "fmi" renamed to "fmi2" (decision from April 8)
#    - Mar   31, 2014: New datatype fmiChar introduced.
#    - Feb.  17, 2013: Changed fmiTypesPlatform from "standard32" to "default".
#                      Removed fmiUndefinedValueReference since no longer needed
#                      (because every state is defined in ScalarVariables).
#    - March 20, 2012: Renamed from fmiPlatformTypes.h to fmiTypesPlatform.h
#    - Nov.  14, 2011: Use the header file "fmiPlatformTypes.h" for FMI 2.0
#                      both for "FMI for model exchange" and for "FMI for co-simulation"
#                      New types "fmiComponentEnvironment", "fmiState", and "fmiByte".
#                      The implementation of "fmiBoolean" is change from "char" to "int".
#                      The #define "fmiPlatform" changed to "fmiTypesPlatform"
#                      (in order that #define and function call are consistent)
#    - Oct.   4, 2010: Renamed header file from "fmiModelTypes.h" to fmiPlatformTypes.h"
#                      for the co-simulation interface
#    - Jan.   4, 2010: Renamed meModelTypes_h to fmiModelTypes_h (by Mauss, QTronic)
#    - Dec.  21, 2009: Changed "me" to "fmi" and "meModel" to "fmiComponent"
#                      according to meeting on Dec. 18 (by Martin Otter, DLR)
#    - Dec.   6, 2009: Added meUndefinedValueReference (by Martin Otter, DLR)
#    - Sept.  9, 2009: Changes according to FMI-meeting on July 21:
#                      Changed "version" to "platform", "standard" to "standard32",
#                      Added a precise definition of "standard32" as comment
#                      (by Martin Otter, DLR)
#    - July  19, 2009: Added "me" as prefix to file names, added meTrue/meFalse,
#                      and changed meValueReferenced from int to unsigned int
#                      (by Martin Otter, DLR).
#    - March  2, 2009: Moved enums and function pointer definitions to
#                      ModelFunctions.h (by Martin Otter, DLR).
#    - Dec.  3, 2008 : First version by Martin Otter (DLR) and
#                      Hans Olsson (Dynasim).
#    Copyright � 2008-2011 MODELISAR consortium,
#                2012-2013 Modelica Association Project "FMI"
#                All rights reserved.
#    This file is licensed by the copyright holders under the BSD 2-Clause License
#    (http:www.opensource.org/licenses/bsd-license.html):
#    ----------------------------------------------------------------------------
#    Redistribution and use in source and binary forms, with or without
#    modification, are permitted provided that the following conditions are met:
#    - Redistributions of source code must retain the above copyright notice,
#      this list of conditions and the following disclaimer.
#    - Redistributions in binary form must reproduce the above copyright notice,
#      this list of conditions and the following disclaimer in the documentation
#      and/or other materials provided with the distribution.
#    - Neither the name of the copyright holders nor the names of its
#      contributors may be used to endorse or promote products derived
#      from this software without specific prior written permission.
#    THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
#    "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED
#    TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR
#    PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR
#    CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL,
#    EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO,
#    PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS;
#    OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
#    WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR
#    OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF
#    ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#    ----------------------------------------------------------------------------
#    with the extension:
#    You may distribute or publicly perform any modification only under the
#    terms of this license.
#    (Note, this means that if you distribute a modified file,
#     the modified file must also be provided under this license).
# 
#  Platform (unique identification of this header file)
#  Type definitions of variables passed as arguments
#    Version "default" means:
#    fmi2Component           : an opaque object pointer
#    fmi2ComponentEnvironment: an opaque object pointer
#    fmi2FMUstate            : an opaque object pointer
#    fmi2ValueReference      : handle to the value of a variable
#    fmi2Real                : double precision floating-point data type
#    fmi2Integer             : basic signed integer data type
#    fmi2Boolean             : basic signed integer data type
#    fmi2Char                : character data type
#    fmi2String              : a pointer to a vector of fmi2Char characters
#                              ('\0' terminated, UTF8 encoded)
#    fmi2Byte                : smallest addressable unit of the machine, typically one byte.
# 
  fmi2Component* {.impfmuTemplate.} = pointer

#  Pointer to FMU instance
  fmi2ComponentEnvironment* {.impfmuTemplate.} = pointer

#  Pointer to FMU environment
  fmi2FMUstate* {.impfmuTemplate.} = pointer

#  Pointer to internal FMU state
  fmi2ValueReference* {.impfmuTemplate.} = cuint
  fmi2Real* {.impfmuTemplate.} = cdouble
  fmi2Integer* {.impfmuTemplate.} = cint
  fmi2Boolean* {.impfmuTemplate.} = cint
  fmi2Char* {.impfmuTemplate.} = cchar
  fmi2String* {.impfmuTemplate.} = ptr fmi2Char
  fmi2Byte* {.impfmuTemplate.} = cchar
  fmi2CallbackLogger* {.impfmuTemplate.} = proc(a1: fmi2ComponentEnvironment, a2: fmi2String, a3: fmi2Status, a4: fmi2String, a5: fmi2String) {.cdecl.}
  fmi2CallbackAllocateMemory* {.impfmuTemplate.} = proc(a1: cuint, a2: cuint) {.cdecl.}
  fmi2CallbackFreeMemory* {.impfmuTemplate.} = proc(a1: pointer) {.cdecl.}
  fmi2StepFinished* {.impfmuTemplate.} = proc(a1: fmi2ComponentEnvironment, a2: fmi2Status) {.cdecl.}
  fmi2CallbackFunctions* {.impfmuTemplate, bycopy.} = object
    logger*: fmi2CallbackLogger
    allocateMemory*: fmi2CallbackAllocateMemory
    freeMemory*: fmi2CallbackFreeMemory
    stepFinished*: fmi2StepFinished
    componentEnvironment*: fmi2ComponentEnvironment
  fmi2EventInfo* {.impfmuTemplate, bycopy.} = object
    newDiscreteStatesNeeded*: fmi2Boolean
    terminateSimulation*: fmi2Boolean
    nominalsOfContinuousStatesChanged*: fmi2Boolean
    valuesOfContinuousStatesChanged*: fmi2Boolean
    nextEventTimeDefined*: fmi2Boolean
    nextEventTime*: fmi2Real

#  reset alignment policy to the one set before reading this file
#  Define fmi2 function pointer types to simplify dynamic loading
# **************************************************
# Types for Common Functions
# ***************************************************
#  Inquire version numbers of header files and setting logging status
  fmi2GetTypesPlatformTYPE* {.impfmuTemplate.} = proc(): cstring {.cdecl.}
  fmi2GetVersionTYPE* {.impfmuTemplate.} = proc(): cstring {.cdecl.}

#  Creation and destruction of FMU instances and setting debug status
  fmi2InstantiateTYPE* {.impfmuTemplate.} = proc(a1: fmi2String, a2: fmi2Type, a3: fmi2String, a4: fmi2String, a5: ptr fmi2CallbackFunctions, a6: fmi2Boolean, a7: fmi2Boolean): fmi2Component {.cdecl.}
  fmi2FreeInstanceTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component) {.cdecl.}

#  Enter and exit initialization mode, terminate and reset
  fmi2SetupExperimentTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2Boolean, a3: fmi2Real, a4: fmi2Real, a5: fmi2Boolean, a6: fmi2Real): fmi2Status {.cdecl.}
  fmi2EnterInitializationModeTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}
  fmi2ExitInitializationModeTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}
  fmi2TerminateTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}
  fmi2ResetTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}

#  Getting and setting variable values
#  Getting and setting the internal FMU state
  fmi2GetFMUstateTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: ptr fmi2FMUstate): fmi2Status {.cdecl.}
  fmi2SetFMUstateTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2FMUstate): fmi2Status {.cdecl.}
  fmi2FreeFMUstateTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: ptr fmi2FMUstate): fmi2Status {.cdecl.}
  fmi2SerializedFMUstateSizeTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2FMUstate, a3: ptr cuint): fmi2Status {.cdecl.}

#  Getting partial derivatives
# **************************************************
# Types for Functions for FMI2 for Model Exchange
# ***************************************************
#  Enter and exit the different modes
  fmi2EnterEventModeTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}
  fmi2NewDiscreteStatesTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: ptr fmi2EventInfo): fmi2Status {.cdecl.}
  fmi2EnterContinuousTimeModeTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}
  fmi2CompletedIntegratorStepTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2Boolean, a3: ptr fmi2Boolean, a4: ptr fmi2Boolean): fmi2Status {.cdecl.}

#  Providing independent variables and re-initialization of caching
  fmi2SetTimeTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2Real): fmi2Status {.cdecl.}

#  Evaluation of the model equations
# **************************************************
# Types for Functions for FMI2 for Co-Simulation
# ***************************************************
#  Simulating the slave
  fmi2DoStepTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2Real, a3: fmi2Real, a4: fmi2Boolean): fmi2Status {.cdecl.}
  fmi2CancelStepTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component): fmi2Status {.cdecl.}

#  Inquire slave status
  fmi2GetStatusTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2StatusKind, a3: ptr fmi2Status): fmi2Status {.cdecl.}
  fmi2GetRealStatusTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2StatusKind, a3: ptr fmi2Real): fmi2Status {.cdecl.}
  fmi2GetIntegerStatusTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2StatusKind, a3: ptr fmi2Integer): fmi2Status {.cdecl.}
  fmi2GetBooleanStatusTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2StatusKind, a3: ptr fmi2Boolean): fmi2Status {.cdecl.}
  fmi2GetStringStatusTYPE* {.impfmuTemplate.} = proc(a1: fmi2Component, a2: fmi2StatusKind, a3: ptr fmi2String): fmi2Status {.cdecl.}

#  ---------------------------------------------------------------------------
#  Function calls allowed state masks for both Model-exchange and Co-simulation
#  ---------------------------------------------------------------------------
#  ---------------------------------------------------------------------------
#  Function calls allowed state masks for Model-exchange
#  ---------------------------------------------------------------------------
#  ---------------------------------------------------------------------------
#  Function calls allowed state masks for Co-simulation
#  ---------------------------------------------------------------------------
  ModelInstance* {.impfmuTemplate, bycopy.} = object
    r*: ptr fmi2Real
    i*: ptr fmi2Integer
    b*: ptr fmi2Boolean
    s*: ptr fmi2String
    isPositive*: ptr fmi2Boolean
    time*: fmi2Real
    instanceName*: fmi2String
    `type`*: fmi2Type
    GUID*: fmi2String
    functions*: ptr fmi2CallbackFunctions
    loggingOn*: fmi2Boolean
    logCategories*: array[4, fmi2Boolean]
    componentEnvironment*: fmi2ComponentEnvironment
    state*: ModelState
    eventInfo*: fmi2EventInfo
    isDirtyValues*: fmi2Boolean
    isNewEventIteration*: fmi2Boolean



#  end of extern "C" {
# 
#   Export FMI2 API functions on Windows and under GCC.
#   If custom linking is desired then the FMI2_Export must be
#   defined before including this file. For instance,
#   it may be set to __declspec(dllimport).
# 
#  Macros to construct the real function name
#    (prepend function name by FMI2_FUNCTION_PREFIX)
# **************************************************
# Common Functions
# ***************************************************
# **************************************************
# Functions for FMI2 for Model Exchange
# ***************************************************
# **************************************************
# Functions for FMI2 for Co-Simulation
# ***************************************************
#  Version number
# **************************************************
# Common Functions
# ***************************************************
#  Inquire version numbers of header files
#  Creation and destruction of FMU instances
#  Enter and exit initialization mode, terminate and reset
#  Getting and setting variables values
#  Getting and setting the internal FMU state
#  Getting partial derivatives
# **************************************************
# Functions for FMI2 for Model Exchange
# ***************************************************
#  Enter and exit the different modes
#  Providing independent variables and re-initialization of caching
#  Evaluation of the model equations
# **************************************************
# Functions for FMI2 for Co-Simulation
# ***************************************************
#  Simulating the slave
#  Inquire slave status
#  end of extern "C" {
#  macros used to define variables
proc setString*(comp: fmi2Component, vr: fmi2ValueReference, value: fmi2String): fmi2Status {.impfmuTemplateC.}

```
