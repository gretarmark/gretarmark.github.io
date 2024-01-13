---
layout: post
title: Boost library for C++ - Installation
published: True
---

Boost is a set of libraries for the C++ programming language that provides support for tasks and structures such as linear algebra, 
pseudorandom number generation, multithreading, image processing, regular expressions, and unit testing.

To include the C++ Boost library [1] staticly in Visual Studio, you need to do the following steps [2]:

1. Start by downloading the latest version at [Boost.org](https://www.boost.org/) and unzip the file. Try to included it as close the C: as possible.
2. Go to the directory where you saved the Boost library file ("C:\...\boost_1_84_0").
3. Open CMD in your computer, I usually just use the "Developer Command Prompt for Visual Studio", run the following code:
   "cd C:\codes\Toolbox\boost_1_84_0"
4. Run the command "bootstrap".
5. When bootstrap has done its work, it will give instruction to next step, for me it tells me to run ".\b2", do that.
   This process will take a time.
7. When the process is finished, it will tell you to include two paths:
  * Compiler Include Path: C:\...\boost_1_84_0
  * Linker Include Path: C:\...\boost_1_84_0\stage\lib
8. Create a C++ project in Visual Studio, go to "properties", "configuration properties", under "C++/General" you should add the compiler include path from step 7
   into "Additional Include Directories". Next you go to "Linker/General" and include the linker path inside of "Additional Library Directories"

Now you should be able to run the following code example in your project. This code will take a number from the user as an input ad return a lambda numbe of that input.

```{C++}
#include <boost/lambda/lambda.hpp>
#include <iostream>
#include <iterator>
#include <algorithm>

int main()
{
    using namespace boost::lambda;
    typedef std::istream_iterator<int> in;

    std::for_each(
        in(std::cin), in(), std::cout << (_1 * 3) << " ");
}
```

Here is an output example:

```{C++}
7
21 9
27 21
63 33
99 104
312 310
930 2
6
```

#### References

[1] Boost library. [Link to reference](https://www.boost.org/)

[2] IQ95 The Homo Siliconiens. Youtube. [Link to reference](https://www.youtube.com/watch?v=5afpq2TkOHc)

