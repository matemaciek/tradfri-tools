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
# Next 2 lines are volatile and may not work with future versions. These hacks are just too ugly.
sed -i "s/#if 0/#if 1/g" ext/tinydtls/sha2/sha2.h
sed -i "17i#include <time.h>" include/coap/coap_time.h
make && make install
```
