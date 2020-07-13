# c_snipet_MinhHieuEC

Some neccessary snipet to program firmware for microcontroller.

## Convert Float to Byte array

Example:

```c
#include <stdio.h>

int main(void) {
  int ii;
  union {
    float a;
    unsigned char bytes[4];
  } thing;

  thing.a = 1.234;
  for (ii=0; ii<4; ii++) 
    printf ("byte %d is %02x\n", ii, thing.bytes[ii]);
  return 0;
}
```

Output:

```c
byte 0 is b6
byte 1 is f3
byte 2 is 9d
byte 3 is 3f
```

Tools:
- Convert From Hex to Float online: https://gregstoll.com/~gregstoll/floattohex/

References:
- https://stackoverflow.com/questions/24420246/c-function-to-convert-float-to-byte-array
- https://stackoverflow.com/questions/21384343/what-is-wrong-with-this-int-to-float-conversion-in-c

## Own powf function

```c
#define POWF(x, y) exp(y * log(x))
```
References:
- https://stackoverflow.com/questions/4518011/algorithm-for-powfloat-float

### Concatenate preprocessor define
```c
#define VERSION_MAJOR 1
#define VERSION_MINOR 0
#define REVISION b
#define _STRINGIFY(x) #x
#define STRINGIFY(x) _STRINGIFY(x)

/* here's the magic */
#define _CONCAT(x,y) x##y
#define CONCAT(x,y) _CONCAT(x,y)
#define VERSION VERSION_MAJOR.CONCAT(VERSION_MINOR,REVISION)

integer version_major = VERSION_MAJOR;
integer version_minor = VERSION_MINOR;
string revision = STRINGIFY(REVISION);
string version_string = STRINGIFY(VERSION);
```
Output:
```
integer version_major = 1;
integer version_minor = 0;
string revision = "b";
string version_string = "1.0b";
```
Reference: https://stackoverflow.com/questions/40677104/concatenate-preprocessor-defines-to-form-a-string
