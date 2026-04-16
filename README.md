Ray Marching Engine (OpenGL)


A real-time ray marching renderer implemented from scratch in C++ using OpenGL.
This project focuses on GPU-driven rendering, signed distance field (SDF) modeling, and shader-based image processing pipelines.



Overview


This renderer uses fragment shader-based ray marching to visualize procedurally defined scenes. All scene geometry is defined implicitly using distance functions, eliminating the need for traditional mesh-based pipelines.


The system is designed to:


Run fully on the GPU.
Minimize CPU-GPU synchronization.
Enable flexible, procedural scene construction.



Core Features


1. Ray Marching Pipeline


Implemented iterative ray marching entirely inside fragment shaders.
Distance field evaluation for highly accurate scene intersection.
Surface normal estimation via finite differences.


2. Signed Distance Functions (SDF)


Primitive shapes: Spheres, boxes, planes.
Composition operations: Union, subtraction, and intersection.
Enables infinite procedural geometry without traditional polygon meshes.


3. Lighting & Shading


Diffuse lighting (Lambertian reflection).
Surface normal computation derived from SDF gradients.
Basic shadow approximation via secondary ray marching.


4. Post-Processing Pipeline


Multi-pass rendering using Framebuffer Objects (FBO).
Fullscreen quad pipeline for screen-space effects.
Sobel edge detection applied on the rendered output for stylized visuals.


5. GPU-Centric Design


Rendering is fully executed within shaders.
Minimal CPU-side logic overhead.
Focuses heavily on parallel execution and memory locality.



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




Demo Videos


Ray Marching Output Demonstration
Post-Processing & Visual Effects



Gallery


Sample Render
Additional Renders



Technical Focus Areas


GPU-based rendering pipelines
Shader programming (GLSL)
Mathematical modeling using SDFs
Multi-pass rendering architectures
Image-space post-processing



Limitations & Future Work


Current Limitations


No acceleration structures (e.g., BVH, spatial partitioning).
Limited material system (no Physically Based Rendering yet).
Shadows are approximate (lacks soft shadow refinement).
No reflections or refractions.


Planned Improvements


[ ] Physically Based Shading (PBR).
[ ] Soft shadows and ambient occlusion.
[ ] Reflections via secondary ray marching.
[ ] Migration to Compute Shaders for better performance and control.



References & Resources


Inigo Quilez — Distance Functions & Ray Marching
Inigo Quilez — Rendering Worlds with Two Triangles
The Book of Shaders — Ray Marching Concepts
LearnOpenGL — Framebuffers
Sebastian Lague — Ray Marching (Conceptual Intro)



Build & Run


Requirements


OpenGL 3.3+
C++ Compiler (GCC / Clang / MSVC)


Steps


# 1. Clone the repository
git clone https://github.com/yourusername/your-repo-name.git

# 2. Navigate to the directory
cd your-repo-name

# 3. Build using your preferred build system (e.g., CMake, Make)

# 4. Run the executable




Notes


Any performance drops or stutters visible in the demo videos are strictly due to screen recording overhead (OBS), not the renderer itself.
