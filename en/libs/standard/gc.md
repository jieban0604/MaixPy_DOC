
gc – control the garbage collector
=======

This module implements a subset of the corresponding CPython module, as described below. For more information, refer to the original CPython documentation: [gc](https://docs.python.org/3.5/library/gc.html#module-gc).

## Functions

### gc.enable()

Enable automatic garbage collection.

### gc.disable()

Disable automatic garbage collection. Heap memory can still be allocated, and garbage collection can still be initiated manually using `gc.collect()`.

### gc.collect()

Run a garbage collection.

### gc.mem_alloc()

Return the number of bytes of heap RAM that are allocated.

#### Difference to CPython

This function is MicroPython extension.

### gc.mem_free()

Return the number of bytes of available heap RAM, or -1 if this amount is not known.

#### Difference to CPython

This function is MicroPython extension.

### gc.threshold([amount])

Set or query the additional GC allocation threshold. Normally, a collection is triggered only when a new allocation cannot be satisfied, i.e. on an out-of-memory (OOM) condition. If this function is called, in addition to OOM, a collection will be triggered each time after amount bytes have been allocated (in total, since the previous time such an amount of bytes have been allocated). amount is usually specified as less than the full heap size, with the intention to trigger a collection earlier than when the heap becomes exhausted, and in the hope that an early collection will prevent excessive memory fragmentation. This is a heuristic measure, the effect of which will vary from application to application, as well as the optimal value of the amount parameter.

Calling the function without argument will return the current value of the threshold. A value of -1 means a disabled allocation threshold.

#### Difference to CPython

This function is a MicroPython extension. CPython has a similar function - `set_threshold()`, but due to different GC implementations, its signature and semantics are different.

