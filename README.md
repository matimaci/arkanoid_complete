# arkanoid_complete

![](https://github.com/matimaci/arkanoid_complete/blob/master/screens/screen3.png)
![](https://github.com/matimaci/arkanoid_complete/blob/master/screens/screen2.png)

#### on Windows 10 just run the [exe file](https://github.com/matimaci/arkanoid_complete/blob/master/win10_x64.exe) (must be in the same directory as res)
#### in case of missing openal dll download and run oalinst.exe from [this site](https://www.gog.com/forum/hotline_miami_series/openal32dll_missing_cant_launch_the_game_101) (first post)

dependencies (headers and libs):
* [sfml-audio](https://github.com/SFML/SFML)
* [GLM](https://github.com/g-truc/glm) (this is only header library)
* [GLFW](https://github.com/glfw/glfw)
* [FreeType](https://www.freetype.org)

[stb_image.h](https://github.com/nothings/stb) and files generated by [glad](https://github.com/Dav1dde/glad) are included in this project.  
All of the art and sound effects come from [opengameart.org](http://opengameart.org).  

### building
Linux Ubuntu:
* sudo apt install libglfw3-dev libfreetype6-dev libsfml-dev libglm-dev
* $ make

Mac && Windows  
follow these guides:
* [Compiling GLFW](http://www.glfw.org/docs/latest/compile_guide.html)
* [Building applications with GLFW](http://www.glfw.org/docs/latest/build_guide.html)
* [SFML Tutorials](http://www.sfml-dev.org/tutorials)

I have succesfully compiled this app without any code tweaking on all three platforms and everything works smooth.

### resolution
Default window size is 800x600. You can change it by passing new width and height as arguments when invoking program (keep the aspect ratio).
It is not possible to change resolution during runtime due to my postprocessing system inflexibility (but there is an easy fix and it will be implemented in next versions / applications).

### performance
Debugging with [apitrace](https://github.com/apitrace/apitrace) did not show any bottlenecks. On linux with Intel HD graphics 520 it runs
with 240 fps (900x700 framebuffer). Postprocessing (bloom mostly) takes most of the frametime.
In future I will definitely use instanced rendering for sprites to limit opengl api calls. I will consider using glMapBufferRange instead
of glBufferSubData when updating particles (or even move them to gpu with transform feedback or compute shader).
