Ray Marching Engine (OpenGL)




Note: This project is currently a work in progress. Large portions of the codebase need cleanup, refactoring, and better documentation. Expect rough edges.




A real-time ray marching renderer built from scratch in C++ with OpenGL, driven entirely through fragment shaders. The project explores GPU-based rendering using Signed Distance Functions (SDFs) and a basic post-processing pipeline.



Demo


Ray Marching Output





Post-Processing & Sobel Edge Detection







Performance drops in the recordings are from OBS screen capture overhead, not the renderer.





What It Does (So Far)


Fragment shader-based ray marching against SDF-defined geometry
Basic primitive shapes: spheres, boxes, planes
SDF composition: union, subtraction, intersection
Lambertian diffuse shading with normal estimation via finite differences
Approximate hard shadows via secondary ray marching
Multi-pass rendering using Framebuffer Objects (FBO)
Sobel edge detection as a post-processing pass on the final output



Rendering Pipeline


[ Scene Definition (SDFs) ]
          |
          v
[ Fragment Shader (Ray Marching) ]
          |
          v
[ FBO (Offscreen Render Target) ]
          |
          v
[ Post-Processing (Sobel Filter) ]
          |
          v
[ Final Output to Screen ]




Build & Run


Requirements


OpenGL 3.3+
C++ compiler (GCC / Clang / MSVC)
GLFW, GLEW (or GLAD)


Steps


git clone https://github.com/novascream/Ray_marcher_using_fragment_shader_in_opengl.git
cd Ray_marcher_using_fragment_shader_in_opengl

# Build with your preferred system (CMake / Make / manual compilation)
# Then run the executable





Build instructions are not fully set up yet — this will be improved.





Known Issues & What Needs Work


This project is far from polished. Here is an honest list of what is lacking:


Code quality


[ ] Shader code is messy and largely uncommented — needs a full cleanup pass
[ ] Magic numbers scattered throughout, need to be extracted into constants/uniforms
[ ] No proper abstraction for shaders, FBOs, or scene objects — everything is fairly tangled
[ ] C++ side has minimal structure, needs refactoring into cleaner classes/modules


Rendering limitations


[ ] No acceleration structures — ray marching against complex scenes is slow
[ ] Shadows are hard and approximate, no soft shadows or ambient occlusion
[ ] No reflections or refractions implemented
[ ] No PBR material system — just basic Lambertian diffuse
[ ] SDF scene composition is hardcoded in the shader, not configurable at runtime


Infrastructure


[ ] No proper CMake / build system setup yet
[ ] No error handling for shader compilation failures
[ ] No camera controls or runtime interaction
[ ] No scene file format — everything is baked into the shader



Planned (Eventually)


Physically Based Shading (PBR)
Soft shadows and ambient occlusion
Reflections via secondary ray marching
Proper camera system with movement
Migration to Compute Shaders for better control and performance
Cleaner codebase with actual documentation



References


Inigo Quilez — Distance Functions
Inigo Quilez — Rendering Worlds with Two Triangles
The Book of Shaders
LearnOpenGL — Framebuffers
Sebastian Lague — Coding Adventure: Ray Marching
