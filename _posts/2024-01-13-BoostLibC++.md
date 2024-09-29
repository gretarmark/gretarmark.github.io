---
layout: post
title: Getting started with Boost library for C++
published: True
---

Boost is a collection of libraries for the C++ programming language that provides support for various tasks and structures, including linear algebra, 
pseudorandom number generation, multithreading, image processing, regular expressions, and unit testing.

# Steps to include the C++ Boost library in Visual Studio

To include the Boost library [1] statically in Visual Studio, follow these steps [2]:

1. Downloading and Unzip Boost
  *  Start by downloading the latest version from [Boost.org](https://www.boost.org/)
  *  Unzip the downloaded file and place it as close to the root of the C: drive as possible (e.g., "C:\...\boost_1_84_0").
2. Ioen the Command Prompt
  * Open the Command Prompt (CMD) on your computer. I recommend using the "Developer Command Prompt for Visual Studio"
  * Navigate to the Boost directiory using the following command: "cd C:\codes\Toolbox\boost_1_84_0"
3. Run Bootstrap
  * Execute the "bootstrap" command.
  * Once bootstrap has completed, it will provide instructions for the next steps. For example, it may instruct you to run ".\b2", do that.
  * This process may take some time to complete.
4. Note the paths provided
  * After the process finishes, it will specify two paths to include in your project:
    * Compiler Include Path: C:\...\boost_1_84_0
    * Linker Include Path: C:\...\boost_1_84_0\stage\lib
5. Create a C++ project in Visual Studio
  * Go to "properties" > "configuration properties".
    * Under "C++/General", add the compiler include path from step 4 into "Additional Include Directories".
    * Under "Linker/General", add the linker path to "Additional Library Directories"
6. Run Example Code
  * You should now be able to run the following example code in your project. This code takes a number from the user as input and returns the lambda number.

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

## Output example:

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

