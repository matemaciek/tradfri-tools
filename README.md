# tradfri-tools
Tools and documentation for remote controlling the IKEA TRÅDFRI smart home system in a sane way

## Building libcoap under Alpine Linux with COAPS/DTLS support

Initially follow the build instructions kindly shared by [Hedda](https://github.com/bwssytems/ha-bridge/issues/570#issuecomment-292081839):

```
git clone --recursive https://github.com/obgm/libcoap.git
cd libcoap
git checkout dtls
git submodule update --init --recursive
./autogen.sh
./configure --disable-documentation --disable-shared
```

In `ext/tinydtls/sha2/sha2.h`, remove the `#if 0/endif` parts:

```
#if 0¬
typedef unsigned char u_int8_t;| |  /* 1-byte  (8-bits)  */¬
typedef unsigned int u_int32_t;| |  /* 4-bytes (32-bits) */¬
typedef unsigned long long u_int64_t;| /* 8-bytes (64-bits) */¬
#endif¬
```

In `include/coap/coap_time.h`, put the following import statement at the top of the file:

`#include <time.h>`

Now finish the installation:

```
make && make install
```
