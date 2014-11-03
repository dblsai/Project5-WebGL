-------------------------------------------------------------------------------
CIS565: Project 5: WebGL
-------------------------------------------------------------------------------

Latest version of Firefox is required for this project.  
Part 1 is an implementation of a sin-shaded moving wave by GLSL vertex shading and fragment shading.  

Part 2 is an implementation of a GLSL fragment shader to render an interactive globe in WebGL.  


-------------------------------------------------------------------------------
PART 1 WebGL Vertex Wave
-------------------------------------------------------------------------------
a dynamic wave animation using code that runs entirely on the GPU.


**Height Shading**

The vertex grid will bw shaded based on height, and the colors chosen by user.
The maxima will be shaded with `highColor`, and the minima will be shaded with `lowColor`
![Height Shading](myPics/height_shading.png)

Click Here for [Live Demo Page](https://github.com/dblsai/Project5-WebGL/vert_wave.html)


 
**My Shading**
I did the shading in the same file as first shading. And this time I include a drop-down menu to select between shading modes.
In the drop-down menu, choose 'normal' or 'mine' to switch between height shading, and my shading mode.

![Height Shading](myPics/my_shading.png)
In the vertex shader, find the property of a vertex:
```
xCol = clamp(position.x,0.0,1.0);
yCol = clamp(position.y,0.0,1.0);
zCol = clamp(height,0.0,1.0);
```

In the fragment shader, the color of a vertex is determined as follows:
```gl_FragColor = vec4(xCol, yCol, zCol, 1.0);```

Hence, the vertex is shading by its position.

**Another Vertex Shader: Perlin Noise**
reference: http://stackoverflow.com/questions/4200224/random-noise-functions-for-glsl
![Perlj=in Noise](myPics/custom_wave2.png)

**Mouse Interaction**
I migrated the mouse interaction from Globe to here. This add more interactivity to the simulation.


-------------------------------------------------------------------------------
PART 2 Globe
-------------------------------------------------------------------------------

* Bump mapped terrain
* Rim lighting to simulate atmosphere
* Night-time lights on the dark side of the globe
* Specular mapping
* Moving clouds

You are also required to pick one open-ended effect to implement:

* Procedural water rendering and animation using noise 
* Shade based on altitude using the height map
* Cloud shadows via ray-tracing through the cloud map in the fragment shader
* Draw a skybox around the entire scene for the stars
Reference: http://www.script-tutorials.com/webgl-with-three-js-lesson-5/
http://math.hws.edu/eck/cs424/notes2013/webgl/skybox-and-reflection/skybox.html


![The Final Globe](myPics/my_globe.png)





-------------------------------------------------------------------------------
PERFORMANCE EVALUATION
-------------------------------------------------------------------------------
Vertex Wave: ~60 fps
Custom Perlin Noise Wave: ~56 fps

-------------------------------------------------------------------------------
REFERENCES
-------------------------------------------------------------------------------
Perlin Noise & Simplex Noise: http://stackoverflow.com/questions/4200224/random-noise-functions-for-glsl
A Very Good FPS recorder:  https://github.com/mrdoob/stats.js
SKYBOX: http://stackoverflow.com/questions/10079368/how-would-i-do-environment-reflection-in-webgl-without-using-a-library-like-thre/10093646#10093646
SKYBOX:   http://math.hws.edu/eck/cs424/notes2013/webgl/skybox-and-reflection/skybox.html 
SKYBOX:   http://www.script-tutorials.com/webgl-with-three-js-lesson-5/ 