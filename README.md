# Fluid Simulation

##(1) SPH 3D Real-Time Fluid Simulation ##

folked from https://github.com/saeedmahani/SPH-3D-Fluid-Simulation

<p align="left">
    <img src="sph_demo.gif", width="240">
    <br>
</p>

Compile:

修改了windows环境下编译的头文件依赖， visual studio 2019 验证。

先编译 freeglut 并 install 到指定文件夹。cmake freeglut 时改掉默认的 install prefix。

编译出 main_project.exe 后，把 freeglut install/bin/ 里的内容都 copy 到 main_project.exe 同文件夹。


----------ORIGINAL README-----------

For our final project in Theodore Kim's Physics-Based Simulation class (Winter '12) we were asked to implement a large, non-trivial technique. My project is based on Matthias Müller's (et al.) research of applying Smoothed Particle Hydrodynamics (SPH) to fluid simulation - essentially simulating fluid as thousands of small particles, rather than the traditional Eularian grid-based approach.

Feel free to email me and I'll tell you more about this project!

## Using the Simulator ##

Firstly, click & drag to rotate the scene using typical GLVU camera controls. You'll notice the simulation starts in a stopped state - you'll need to toggle the animation ON. Below are some keyboard controls.

### Basic Controls ###

a -- Toggle the physics animation on/off (upon starting animation is OFF)  
1 -- Load the "Dam Break" scenario (initial scenario)  
2 -- Load the "Cube" scenario  
3 -- Load the "Faucet" scenario  
t -- Toggle tumble mode on/off (the water will react to the tilt of the camera)  

### Advanced Controls ##
  
g -- Toggle grid visible (grid used for neighbor particle optimization)  
/ -- Toggle gravity on/off  
s -- Toggle coloring of surface purple (particles on the surface have a surface tension force applied)  
f -- Output current FPS to stdout  


## References ##

Particle-Based Fluid Simulation for Interactive Applications  
Matthias Müller, David Charypar and Markus Gross  
https://matthias-research.github.io/pages/publications/sca03.pdf