## One binary instrumentation pass to rule them all, by chqmatteo
### Benefits and costs of using timeless debugging to power dynamic program analyses

Triaging a software bugs can be challeging especially now that fuzzers produce more and more hard to understand crashes. 

Dynamic analysis instrumentation passes (valgrind, sanitizers, ...) can be used to provide more context around a crash with little overhead, but only for certain classes of bugs. 

Record replay (RR) debugging* can be used to record a program execution trace and inspect the program state of the same trace over and over. However debugging sessions can feel overwhelming due to the length of the program trace or the convoluted dataflow or controlflow.

We can try to get the best of both worlds using analyses that work on the recorded program traces instead of instrumenting a program so that we can use the RR debugger to further inspect the points of interest found by the dynamic analyses.

In this talk we will explore some of the benefits and limitations of analyses that work on a timeless trace compared to dynamic instrumentation.

We will use a flavour of timeless debugging** that allows fast random access to the program state at any point in time at the expense of higher disk and memory usage. 
We will build some common fault localization analyses on top of the timeless debugger as case study.

----------

*One big weakness of traditional debuggers is that you need to know a priori where to stop the program to inspect it and there is a high price to pay if the program goes past that point (i.e. you need to restart almost everything from scratch).
Record replay (RR) debuggers can help address some of these issues as they first record some information that can help them to replay an execution trace and then allow you to debug the same execution trace any number of times and also to move to a previous program point in time.

**Similar timeless debuggers that work on binaries are Reven by Tetrane, rr with Pernosco, qira by geohot

Slides link: https://chq-matteo.github.io/one-instrumentation-pass/
