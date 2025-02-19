# CO2: Carbon-Dioxide Thermophysical Property Calculation

# 1. Background

The thermophysical properties of CO2 are very important to researchers and engineers in various domains (energy, power, chemistry, materials ...).

Usually, researchers and engineers rely on the [NIST Refprop](https://www.nist.gov/srd/refprop) to calculate the properties. However, Refprop is commercial and not open-source. Therefore, I wrote this code to provide an alternative to the Refprop.

# 2. Brief Intro

**Program Name**: High-resolution CO2 (Carbon Dioxide) Properties Calculation

**Purpose**: Calculate the **very-high-resolution** thermophysical properties at given point(s)

**License**: MIT

**Technical Reference**:

- R. Span, W. Wagner, A New Equation of State for Carbon Dioxide Covering the Fluid Region from the Triple –Point Temperature to 1100K at Pressures up to 800MPa, J. Phys. Chem. Ref. Data, Vol 25, No.6, 1996
- Marcia L Huber, Marc J Assel, R. A. Perkins, Reference Correlation of the Thermal Conductivity of Carbon Dioxide from the Triple Point to 1100K and up to 200MPa. Joursssnal of Physical and Chemical References Date. Feb. 2016
- William A. Wakeham, The Viscosity of Carbon Dioxide, Journal of Physical and Chemical Reference Data, Jan, 1998.

# 3. How-To: Build, Run, and Use

## 3.1 Build

### 3.1.1 Prerequisites

You need a C compiler to build. 

- For Microsoft Windows users, [mingw](https://sourceforge.net/projects/mingw/) is a good choice
- For GNU/Linux Distro or other *nix users, the [GNU Compiler Collections](https://gcc.gnu.org/), known as gcc, is a perfect one
- For macOS users, [clang](https://clang.llvm.org/) is easy to install and use (brew is not needed to install clang on macOS).

### 3.1.2 Build Guide

1. Use git to clone this code: `git clone https://github.com/zhenrong-wang/co2.git`
2. Build command example: `gcc *.c -o my-co2.exe -lm`

**Note**: the `-lm` may not be valid for Windows or macOS. It is necessary for GNU/Linux distros.

## 3.2 Run

### Run the Test Data

Suppose you have followed the steps above and built the my-co2.exe in the source code folder.

- `cd test`
- `../my-co2.exe` (**UNIX-like OS**) or `..\my-co2.exe` (**Microsoft Windows**)

If you see the output below, congrats, you've built the binary successfully.

    ...

    # Please press ENTER to start calculation:

    1       100000.00000000 320.00000000

    # Calculation finished. Please check _properties.dat for results.
    # Press any key to exit.

    @ Any problems found, please contact the author.
    @ Zhenrong Wang, zhenrongwang@live.com.

### An Example for UNIX-like OS:

Suppose the working directory is `/home/amber/co2`

Suppose the absolute path of the executable is `/home/amber/bin/my-co2.exe`

- `$ cd /home/amber/co2`
- `$ vim _input.dat` # Create an input file named '**_input.dat**' with some input data (See Section 3.3 below)
- `$ /home/amber/bin/my-co2.exe`

### An Example for Windows:

Suppose the working directory is `C:\Users\amber\co2`

Suppose the absolute path of the executable is `C:\Users\amber\bin\my-co2.exe`

- Open a Command Prompt Window
- `cd C:\Users\amber\co2`
- `notepad _input.dat`
- `C:\Users\amber\bin\my-co2.exe`

## 3.3 Use

For the **_input.dat** file, you need to input the data in lines. A single line refers to a point. Strict format:

`POINT_TYPE(int),PARAM1(float/double),PARAM2 (float/double)` 

**Please separate the params by a comma ','**

POINT_TYPE: 

- 1 Pressure and Temperature
- 2 Pressure and Specific Enthalpy
- 3 Pressure and Specific Entropy
- 4 Specific Enthalpy and Specific Entropy
- 5 Temperature and Density
- 6 Pressure and Density
- 7 Temperature and Specific Enthalpy
- 8 Temperature and Specific Entropy

Example: `1,100000,300`

Example: `1,1e5,3e2`

Units:

- Pressure: Pa
- Temperature: K
- Density: kg/m3
- Specific Enthalpy: J/kg
- Specific Entropy: J/(kg.K)

## 3.4 Output

The program writes out a file named '**_properties.dat**' in the working directory. Here are some extra properties:

- Vsound: Velocity of sound
- V_FRAC: The mass ratio of gas when the point is in dual-phase
- VISC: Viscosity
- THCOND: Thermal Conductivity ratio

# 4 Bugs and Communications

This code was written years ago, and I didn't continuously develop it. Therefore, bugs may occur. 

If you are interested in this project, please submit issues to this repo. I'd be glad to communicate on any issues.

Or, you can also email me: zhenrongwang@live.com
