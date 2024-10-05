---
layout: post
title: Installing the Nlopt Library for C++ using vcpkg
published: True
---

**Vcpkg** is an open-source cross-platform package manager developed by Microsoft. 
It simplifies the process of acquiring and managing libraries for C and C++ development. 
This tool helps developers download and install the necessary libraries for their projects,
making it easier to set up and maintain the development environment.

In this post, I'll guide you through installing and using the **Nlopt** [2] optimization library with **Vcpkg** [1] 
for a C++ project in Visual Studio.

# Step-by-Step Installation

For installation I followed the instructions in [3] and for testing the library I used a code example from [4].

1. **Install Vcpkg:** Download and install vcpkg from the official repository [1]. Choose a directory for the vcpkg folder. 
I used **C:\codes\Toolbox\vcpkg** for this guide.
2. **Open PowerShell:** Open Windows PowerShell in your vcpkg folder. 
You can right-click inside the **"C:\codes\Toolbox\vcpkg** folder and choose "Open in Terminal".
Make sure the terminal is in the correct directory.
3. **Run Integration Command:** Execute the following command to integrate vcpkg with CMake: **./vcpkg integrate install**. 
This command will return a line similar to: **-DCMAKE_TOOLCHAIN_FILE=CcodesToolboxvcpkgscriptsbuildsystemsvcpkg.cmake**.
Save this command in a text file for future reference. You can call the file **CMAKE.txt**
4. **Check for NLopt Package:** To see if the NLopt library is available, run: **.\vcpkg search nlopt**. 
You can also search directly on the vcpkg website [2].
5. **Install NLopt:** Install the NLopt library by running: **.\vcpkg install nlopt**. 
The library will be downloaded and installed automatically. 
6. **Manage Installed Packages:** Installed packages are located in **C:\codes\Toolbox\vcpkg\installed**, and you can see the files
for each package in the **C:\codes\Toolbox\vcpkg\packages** directory.
7. **Upgrading or Removing Packages:**
  * To upgrade a package: **.\vcpkg upgrade nlopt**.
  * Or to force an upgrade: **.\vcpkg upgrade nlopt --no-dry-run**.
  * To remove a package: **.\vcpkg remove nlopt"**.
    Use the **--recurse** flag for deeper removal: **.\vcpkg remove nlopt --recurse**.

# Setting up NLopt in Visual Studio 
<!-- Er kominn hingað -->

1. **Create a new project** 
2. **Integrate vcpkg into the project:** Run the following command in PowerShell: **.\vcpkg integrate project** and make sure to add **#include <nlopt>** to your code. Copy the generated command, which should look something like this: **"Install-Package "vcpkg.C.codes.Toolbox.vcpkg" -Source "C:\codes\Toolbox\vcpkg"**.
Open Visual Studio, navigate to **Tools -> NuGet Package Manager -> Package Manager Console**, and paste the command there. 
This will install the vcpkg package in your project.

# Test the Installation with a Sample Code

Here's a sample optimization problem using NLopt. You can test your installation with this code [4]:

```{C++}
#include <iostream>
#include <math.h>
#include <nlopt.h>
#include <stdio.h>

double costFunction(unsigned n, const double* x, double* grad, void* data);

int main()
{
    double lb[2] = { -5.0, -5.0 }; //lower bounds
    double ub[2] = { 5.0 , 5.0 }; //upper bounds

    // create the optimization problem
    // opaque pointer type
    nlopt_opt opt;
    opt = nlopt_create(NLOPT_LD_MMA, 2);

    nlopt_set_lower_bounds(opt, lb);
    nlopt_set_upper_bounds(opt, ub);

    nlopt_set_min_objective(opt, costFunction, NULL);

    nlopt_set_xtol_rel(opt, 1e-4);

    // initial guess
    double x[2] = { 0.0,0.0 };
    double minf;

    nlopt_result res = nlopt_optimize(opt, x, &minf);


    if (res < 0) {
        printf("nlopt failed!\n");
    }
    else {
        printf("found minimum at f(%g,%g) = %0.10g\n", x[0], x[1], minf);
    }
}

double costFunction(unsigned n, const double* x, double* grad, void* data)
{
    // define the gradient vector
    if (grad)
    {
        grad[0] = 2 * (x[0] - 2);
        grad[1] = 2 * (x[1] - 3);
    }

    // return value is the value of the cost function 

    return ((x[0] - 2) * (x[0] - 2) + (x[1] - 3) * (x[1] - 3));
}
```

When you run this code, you should get an output similar to:

**found minimum at $$f(2,3) = 3.790613212e-16$$ \approx 0**

#### Reference

[1] Vcpkg. Homepage. [Link to reference](https://vcpkg.io/en/index.html)

[2] Nlopt Library. [Link to reference](https://nlopt.readthedocs.io/en/latest/)

[3] TroubleChute. Youtube. [Link to reference](https://www.youtube.com/watch?v=0h1lC3QHLHU)

[4] Aleksander Haber. Website. [Link to reference](https://aleksandarhaber.com/solve-optimization-problems-in-c-c-by-using-nlopt-library/)
