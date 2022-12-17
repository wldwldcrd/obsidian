## Project flow
1. Create a platform project - contains default FSBL, PMU and domain
2. You can add multiply domens to platform and create FSBL like any other application.
3. ELF - Executable and Linkable Format
#research FreeRTOS “HelloWorld” example (ug1137 p32)
#research Zynq UltraScale+ MPSoC QEMU User Guide (UG1169)
### Decive Tree Generator
Generates:
• pl.dtsi : Contains all the memory mapped peripheral logic (PL) IPs.
• pcw.dtsi: Contains the dynamic properties for the PS IPs.
• system-top.dts: Contains the memory, boot arguments, and command line
parameters.
• zynqmp.dtsi: Contains all the PS specific and the CPU information.
• zynqmp-clk-ccf.dtsi: Contains all the clock information for the PS peripheral IPs.
#research  Build Device Tree Blob page on the Xilinx Wiki https://xilinx-wiki.atlassian.net/wiki/spaces/A/pages/18842279/Build+Device+Tree+Blob

### Hardware platform project
Contains:
1. .project: Project file
2. psu_init.tcl: PS initialization script
3. psu_init.c,psu_init.h: PS initialization code
4. psu_init.html: Register summary viewer
5. system.hdf: Hardware definition file
# Bare-Metal
Drivers: `<Xilinx InstallationDirectory>\Vitis\<version>\data\embeddedsw\XilinxProcessorIPLib\drivers`
Libraries: `<Xilinx Installation Directory>\Vitis\<version>\data\embeddedsw\lib\sw_services`
## The C Standard Library (libc)
1. alloca.h Allocates space in the stack
2. assert.h Diagnostics code
3. ctype.h Character operations
4. errno.h System errors
5. inttypes.h Integer type conversions
6. math.h Mathematics
7. setjmp.h Non-local goto code
8. stdint.h Standard integer types
9. stdio.h Standard I/O facilities
10. stdlib.h General utilities functions
11. time.h Time function
## The C Standard Library Mathematical Functions (libm)
1. Algebraic cbrt, hypot, sqrt
2. Elementary transcendental asin, acos, atan, atan2, asinh, acosh, atanh, exp, expm1, pow, log, log1p, log10, sin, cos, tan, sinh, cosh, tanh
3. Higher transcendentals j0, j1, jn, y0, y1, yn, erf, erfc, gamma, lgamma, and gamma_ramma_r
4. Integral rounding eil, floor, rint
5. IEEE standard recommended copysign, fmod, ilogb, nextafter, remainder, scalbn, and fabs
6. IEEE classification isnan
7. Floating point logb, scalb, significand
8. User-defined error handling routine matherr
## Standalone BSP
The libraries available with the standalone BSP are as follows:
1. XilFatFS: Is a LibXil FATFile system and provides read/write access to files stored on a Xilinx system ACE compact flash.
2. XilFFS: Generic Fat File System Library.
3. XilFlash: Xilinx flash library for Intel/AMD CFI compliant parallel flash.
4. XilISF: In-System Flash library that supports the Xilinx in-system flash hardware.
5. XilMFS: Memory file system.
6. XilSecure: Xilinx Secure library provides support to access secure hardware (AES, RSA and SHA) engines.
7. XilSkey: Xilinx secure key library.
8. lwIP Library: An open source TCP/IP protocol suite that provides access to the core
9. lwIP stack and BSD (Berkeley Software Distribution) sockets style interface to the stack.
# OS
## Software Stack

## PetaLinux
### Tools installation
sudo chmod -R 777
Install requirements
	gawk
	xterm
	autoconf
	libtool
	texinfo
	gcc-multilib
#### Configuration
project-spec/configs/config
### Components
* **GNU** - Arm GNU tools.
* **petalinux-build** - Used to build software image files.
* **Make** - Make build for compiling the applications.
* **GDB** - GDB tools for debugging.
* **petalinux-boot** - Used to boot Linux.
* **QEMU** - Emulator platform for the Zynq UltraScale+ MPSoC device.
	* Zynq UltraScale+ MPSoC QEMU User Guide (UG1169) #research
* **OProfile** - Used for profiling
Docs:
* Zynq UltraScale+ MPSoC: Embedded Design Tutorial (UG1209)
* Zynq UltraScale+ MPSoC OpenAMP Getting Started Guide (UG1186)
## Yocto
http://git.yoctoproject.org/cgit/cgit.cgi/meta-xilinx/
![[Yocto Tools.png]]
![[Yocto Dev Environment.png]]
* #research Xilinx-provided Yocto features: PetaLinux Tools Documentation: Reference Guide (UG1144)
* Yocto Project https://www.yoctoproject.org/downloads

## Docs
* Vitis Unified Software Platform Documentation: Embedded Software Development (UG1400)
* PetaLinux Tools Documentation: Reference Guide (UG1144)
* Vivado Design Suite Tutorial: Embedded Processor Hardware Design (UG940)
* Zynq UltraScale MPSoC Processing System LogiCORE IP Product Guide (PG201)
* PetaLinux Tools Documentation: Reference Guide (UG1144)
* Bootgen User Guide (UG1283) #research 