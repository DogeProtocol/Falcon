## Falcon
Falcon is a Post Quantum Digital Signature Scheme that has been standardized by NIST.
This repository is based on the [Round 3](https://csrc.nist.gov/Projects/post-quantum-cryptography/post-quantum-cryptography-standardization/round-3-submissions) submission of Falcon. 
New functions have been added to work with the *Doge Protocol Blockchain*.

### Source
[https://csrc.nist.gov/CSRC/media/Projects/post-quantum-cryptography/documents/round-3/submissions/Falcon-Round3.zip](https://csrc.nist.gov/CSRC/media/Projects/post-quantum-cryptography/documents/round-3/submissions/Falcon-Round3.zip)

```SHA256: fd58f0454f6bfb4713734e60b2d2d75d96fbae62d5180fceeef1039df5362f44```

## Changes made for Doge Protocol

Two new functions, `crypto_sign_signature_with_key` and `crypto_sign_verify` functions 
have been added in the *reference implementation* for `falcon512`. 
In subsequent iterations, these changes will be removed in favor of maintaining 
all changes outside of the core cryptography libraries. 

These changes have been primarily added for generating WebAssemblies for use in Browser Extensions.

## Notes

Each implementation under `Reference_Implementation` and
`Optimized_Implementation` has its own Makefile; when used, it compiles
the code along with the test vector generator in `KAT/generator/`. The
resulting binary (created in a subdirectory called `build`), when
executed, produced the .req and .rsp files, which should be identical
to the ones provided in `KAT/`.

The *cxm4 implementations are for the ARM Cortex M4, a CPU normally
found in microcontrollers. Cross-compilation is normally used for such
implementations. The Makefiles invoke the compiler under the name
`arm-linux-gcc` and expect that compiler to come with a minimal but
functional libc; moreover, the use of inline assembly follows the syntax
extensions supported by GCC and Clang. The [Buildroot project](https://buildroot.org/) can be used to obtain an appropriate
cross-compilation toolchain. The resulting binary can be executed under
emulation with [QEMU](https://www.qemu.org/).

All other implementations assume a native C compiler which is invoked
with the command name 'c99' and flags '-W -Wall -O2'.

The implementation in `Extra/c/` has its own Makefile; it compiles into
two command-line tools, `test_falcon` and `speed`. `test_falcon` runs
some self-tests. `speed` runs some benchmarks.


## Contributing

Thank you for considering to help out with the source code! 

* Please reach out in [our Discord Server](https://discord.gg/bbbMPyzJTM) for any questions. 
* Pull requests need to be based on and opened against the `main` branch.

## License

This Falcon implementation is provided under the MIT license, whose text
is included at the start of every source file.
