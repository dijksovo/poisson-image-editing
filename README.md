# About this library

**PoissonBlend** is a small C++ library providing implementations of image editing methods based on gradient domains. 

# Seamless Cloning

Seamless image cloning attempts to copy an image region from a foreground image onto a background image subject to removal of visual seams. Visual seams occur because of the color mismatch between the two images. In gradient domain methods one fixes the colors of the boundary (taken from the background image) and provides a vector field that defines the structure of the image to be copied (taken from the foreground and / or a mixture from foreground and background). The result image is generated by minimizing the squared error terms between the gradient of the result image and the guidance vector field. 

The function `blend::seamlessClone` implements the method described in [1] providing different options for various guidance field computations. The table below shows a comparison between naively copying foreground over background and seamless copying as implemented by this library.

|  Naive Cloning | Seamless Cloning | 
|:--------------:|:----------------:|
| ![Naive Image Cloning](/etc/results/1/naive.png?raw=true) | ![Seamless Image Cloning](/etc/results/1/mixed-gradients.png?raw=true) |
| ![Naive Image Cloning](/etc/results/2/naive.png?raw=true) | ![Seamless Image Cloning](/etc/results/2/mixed-gradients.png?raw=true) |

# References
[1] Pérez, Patrick, Michel Gangnet, and Andrew Blake. "Poisson image editing." ACM Transactions on Graphics (TOG). Vol. 22. No. 3. ACM, 2003.

# Building from source
To build **PoissonBlend** from source you need the following prerequisites
 - [CMake](www.cmake.org) - for generating cross platform build files
 - [OpenCV](www.opencv.org) - for image processing related functions
 - [Eigen](eigen.tuxfamily.org/) - for sparse linear system solving
 
Although **PoissonBlend** should build across multiple platforms and architectures, tests are carried out on these systems
 - Windows 7/8 MSVC10 x86
 - OS X 10.10 XCode 6.2

If the build should fail for a specific platform, don't hesitate to create an issue. I'm also happy to accept any pull requests.

# License
```
   Copyright Christoph Heindl 2015

   PoissonBlend is free software: you can redistribute it and/or modify
   it under the terms of the GNU General Public License as published by
   the Free Software Foundation, either version 3 of the License, or
   (at your option) any later version.
   
   PoissonBlend is distributed in the hope that it will be useful,
   but WITHOUT ANY WARRANTY; without even the implied warranty of
   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
   GNU General Public License for more details.
   
   You should have received a copy of the GNU General Public License
   along with PoissonBlend.  If not, see <http://www.gnu.org/licenses/>.
```
