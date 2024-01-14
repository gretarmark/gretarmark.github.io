---
layout: post
title: Nlopt library for C++ - Installation using vcpkg
published: True
---

Vcpkg is an open-source cross-platform package manager from Microsoft that simplifies the process of acquiring and managing libraries 
and tools for C and C++ development. It helps developers download and install various libraries and dependencies needed for their projects, 
making it easier to set up and maintain the development environment.
In this post I will explain how to use Vcpkg [1] to install and include the optimization library Nlopt [2] in a Visual Studio project.

For installation I followed the instructions in [3] and for testing the library I used a code example from [4].

1. Install Vcpkg from [1] and choose a good directory for the vcpkg folder. Mine is "C:\codes\Toolbox\vcpkg".
2. Run you windows powershell. It can be done for example by right-click inside of the vcpkg folder and choose open in terminal.
   Make sure you are in the right folder ("vcpkg").
4. Write "./vcpkg integrate install" and you should get command something like this: "-DCMAKE_TOOLCHAIN_FILE=CcodesToolboxvcpkgscriptsbuildsystemsvcpkg.cmake".
5. Save this command in a text file in the vcpkg folder to use it in the future. The text file can be called CMAKE.
6. Write ".\vcpkg search nlopt" to see if you can use vcpkg to install that library. You can also search on the website [2].
7. The nlopt library can be installed using ".\vcpkg install nlopt".
8. Installed packages are found in "C:\codes\Toolbox\vcpkg\installed", but it includes all of the files thrown together.
   To see the separately go to "C:\codes\Toolbox\vcpkg\packages".
9. If needed, packages can be upgraded using ".\vcpkg upgrade nlopt" or ".\vcpkg upgrade nlopt --no-dry-run".
10. Packages can be removed by using ".\vcpkg remove nlopt" or ".\vcpkg remove nlopt --recurse" for more deeper remove.

To set the library up in Visual Studio do the following:
1. Create new project
2. Add "#include <nlopt>" to your C++ code.
3. Run ".\vcpkg integrate project" in Windows Powershell and copy the command you get "Install-Package "vcpkg.C.codes.Toolbox.vcpkg" -Source "C:\codes\Toolbox\vcpkg"".
4. Follow the instructions by going to Visual Studio, "Tools/NuGet Package Manager/Package Manager Console", and paste the command in there.
   This will install the vcpkg project.
5. Now the library should work.

You can try the code from [4]:

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

The output should be "found minimum at $$f(2,3) = 3.790613212e-16$$ \approd 0".

#### Reference

[1] Vcpkg. Homepage. [Link to reference](https://vcpkg.io/en/index.html)

[2] Nlopt Library. [Link to reference](https://nlopt.readthedocs.io/en/latest/)

[3] TroubleChute. Youtube. [Link to reference](https://www.youtube.com/watch?v=0h1lC3QHLHU)

[4] Aleksander Haber. Website. [Link to reference](https://aleksandarhaber.com/solve-optimization-problems-in-c-c-by-using-nlopt-library/)
