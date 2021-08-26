# About

All code is compiled and tested on an ARMv8-A processor running Ubuntu 21.04.


# Contents

## 1. arm64-assembly-hello-world

The folder `arm-assembly-hello-world` contains an ARM64 Assembly program that outputs "Hello World!\n".
It is an adaption of [this](https://peterdn.com/post/2020/08/22/hello-world-in-arm64-assembly/) tutorial.
It was assembled to an object file with `as -o hello-world.o hello-world.s` and then linked with `ld -s -o hello-world hello-world.o`.
With `objdump -D hello-world > hello-world-objdump.txt` a textfile was created, that contains the translation between ARM64 Assembly instructions and machine code instructions.


## 2. arm64-assembly-calc

The folder `arm-assembly-calc` contains a minimalistic ARM64 Assembly program that sets two registers to the values 20 and 22 and then adds the two registers.


## 3. bare-metal-arm64-hello-world

The folder `bare-metal-arm64-hello-world` contains a bare metal ARM64 Assembly program that outputs "Hello World!\n".
It can be compiled with the script `compile.sh`.

### Sources
- https://developer.arm.com/documentation/102432/0100
- https://github.com/freedomtan/aarch64-bare-metal-qemu

## 4. bare-metal-arm64-hello-world-qemu

The folder `bare-metal-arm64-hello-world-qemu` contains the base program used in `bare-metal-arm64-hello-world`.
It is an adaption of [this](https://github.com/freedomtan/aarch64-bare-metal-qemu) repository.
It can be compiled with the script `compile.sh`.
After compiling it, it can be tested with QEMU by issuing `qemu-system-aarch64 -M virt -cpu host -enable-kvm -nographic -kernel hello_world.elf` on a system with an ARM64 processor.
To emulate it on another architecture replace `-cpu host` with `-cpu cortex-a57` for example.

## 5. KVM Test Program

The cpp-file `kvm_test.cpp` contains a program that shall setup an ARM64 VM and execute the bare-metal-arm64-hello-world program in the VM.
As a starting point, [this](https://lwn.net/Articles/658512/) KVM test program for x86 was used.
It is explained [here](https://lwn.net/Articles/658511/).
To change the code from x86 to ARM64 the [KVM API Documentation](https://www.kernel.org/doc/html/latest/virt/kvm/api.html) was used.
