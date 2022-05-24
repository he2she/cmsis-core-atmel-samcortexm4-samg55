
# Note
duplicated from [ARMmbed Repo](https://github.com/ARMmbed/mbed-hal-atmel)  
Change: dependencies are constrained.The following quick fix(Problems) is applied.


# Known issues

## Compile error:

```
In file included from /yotta/atmel-samg55j19-gcc_blinky/yotta_modules/mbed-hal-atmel-samg55j19/source/services/delay/sam/cycle_counter.h:54:0,
                 from /yotta/atmel-samg55j19-gcc_blinky/yotta_modules/mbed-hal-atmel-samg55j19/source/services/delay/sam/cycle_counter.c:47:
/yotta/atmel-samg55j19-gcc_blinky/yotta_modules/cmsis-core-atmel-samcortexm4-samg55/source/compiler.h:239:50: error: 's' undeclared here (not in a function)
 #   define OPTIMIZE_HIGH __attribute__((optimize(s)))
                                                  ^
/yotta/atmel-samg55j19-gcc_blinky/yotta_modules/mbed-hal-atmel-samg55j19/source/services/delay/sam/cycle_counter.c:50:1: note: in expansion of macro 'OPTIMIZE_HIGH'
 OPTIMIZE_HIGH
 ^~~~~~~~~~~~~
ninja: build stopped: subcommand failed.
```

## Quick fix:

```
#elif defined (  __GNUC__  ) /* GCC CS3 2009q3-68 */
#   define OPTIMIZE_HIGH __attribute__((optimize("s"))) //TODO:this is quick fix. auth:Hitoshi Chano. ref:(https://www.avrfreaks.net/forum/latest-atmel-studio-701006-fails-compile-cyclecounterc)
#endif
```