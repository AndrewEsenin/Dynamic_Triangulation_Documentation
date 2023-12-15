# Dynamic Triangulation Documentation

Unreal Marketplace Link:   
YouTube:  
Support email: andrewesenin27@gmail.com  
Example Project:  
Playable Demo: https://drive.google.com/file/d/1-hEs6MUIa3aM4M6qKXNQgG-7sC1zHifS/view?usp=sharing  
  
<br />

<!--ts-->
* [Description](#Description)
* [Quick Start](#Quick-Start)
* [Functions Description](#Functions-Description)
* [Materials](#Materials)
* [Features and Tips](#Features-and-Tips)
* [Example Project](#Example-Project)
<!--te-->

<br />

## Description  
This C++ Plugin will allow you to create polygonal meshes from points.  
Meshes can be created in the editor or when the game is running.   
You can use a set of consecutive points (spline points, for example) that form an area to turn it into a single mesh.  
You can download the [Example Project](#Example-Project), it contains an overview scene and Runtime example.  

<br />

## Quick Start  
1. Install the plugin on your version of the engine.    

![SPT_01](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/f9ae88e2-fff4-47d3-abbf-eb3cb51c0896)


2. Activate the plugin (if not activated) and restart the engine.

![Scr_08](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/61eb06c8-3ddb-4f4f-bf64-aa4f536ea2a4)


3. To access the Blueprint examples, do the following, 
for UE4: 

![Scr_01](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/a3733d98-d716-4245-aaae-e3220b20356d)

   for UE5:  

![Scr_02](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/d066b326-167c-4ace-b36f-8656110f1420)


4. "Dynamic Triangulation Actor" contains all functions for triangulation and edit Points Array.  
You can create your own empty actor or use one of the ready-made examples.

![Scr_03](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/9f22c39f-1dc8-4b02-9659-655c2039b463)


If you want to use Dynamic Triangulation in the editor, simply drag "BP_DT_Editor" ready-made examples onto the level and edit the spline.  
To quickly create points, hold Alt and drag:  

https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/8f0863f2-b76f-4612-ae97-04b5d8c074e7

<br />
If you want to use Dynamic Triangulation at runtime, you can do the following:  
Create a new BP_DT_Runtime using the Spawn Actor from Class function, and connect this node to the Begin Play event (for example in Player Controller).    
Then call the DrawPoly function.  

![Scr_04](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/ae0272d2-fed1-4928-9b75-6b74cf4b465e)  

<br />

## Functions Description   
The plugin includes 3 blueprintcallable functions.  
All functions are located in the "Dynamic Triangulation" section.  

![Scr_07](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/b5974044-b357-47ca-be3a-bf60fbdde7e1)

**Triangulate Polygon**  
Triangulates a specific area that's defined by an array of points.  

| **Parameter** | **Description**  |  
|---------------|------------------|  
| Points | A sequential array of points forming an area for triangulation. |
| bReversePoints | Inverts the order of points in an array. |
| bEnableUV | Enables UV creation, by default the M_DT_Master material uses global coordinates, such a material does not need UVs, but if you need UVs, you can enable it. |
| ScaleUV | Scale UV on two axes, squeezes the texture along one of the axes. |
| Triangles | Array of triangles for Procedural Mesh. |
| UV | Array of UV coordinates for Procedural Mesh. |

<br />

**Rounding Path Corners**  
Rounding the corners of the path.  
The Radius parameter determines the strength of the rounding, and the Segments parameter determines how many polygons will be created at each corner.  
With Segments = 1 it works like a chamfer, just cutting corners, Segments = 8-16 is enough to make smooth and rounded corners.  
It is also handy to use with a small Radius and a value of 1 for Segments to trim very long sharp corners that can occur with sharp path turns.  
bLoopPath in this case looping means that two rounded corners will be added between the first and last point of the path.  

<br />

**Merge Border Points**   
Merges path points that are closer together than MergedDistance.  
If your path has consecutive points with the same coordinates, this function will remove them.  
You can also use this function for optimization, if you have clusters of points along the path,  
you can combine them into one and then, for example, round the corners.  

<br />

## Materials   
The asset includes one main material M_DT_Master.  
All other materials are instances of this one.  
  
<br />
  
**Main Material Parametrs**  
  
![Scr_06](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/4ed4ec53-b865-4fa2-8d5d-99e76b8af993)  

<br />  

| **Parameter** | **Description**  |  
|---------------|------------------|  
| Color | Material color. The material contains two colors with parameters, one color is applied to the black pixels of Alpha, the second to the white ones. |
| Emissive | Glow strength. |
| Opacity | Part material opacity. |
| Enable Flickering | Enables flickering animation. |
| Frequency | Flicker frequency. |
| Intencity Min | Minimum flicker brightness. |
| Intencity Max | Maximum flicker brightness. |
| Alpha | Opacity mask. |
| Texture Tilling | Texture tiling along X and Y axes. |
| Rotate Angle (0-1) | Rotates the Alpha, 1 = 360 degrees. |
| Absolute Coordinate | If enabled, global UV coordinates will be used, useful for meshes that have no or incorrect UVs. |
| Anim Speed X | Texture anim speed along the X axis. |
| Anim Speed Y | Texture anim speed along the Y axis. |   
<br />  

To increase the brightness of the glow, you can increase this value when changing the color of the material or adjust the Emissive values.   
(Also, the brightness of the glow may depend on the post-processing settings)  
  
![SPT_11](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/42d25663-759b-4d3b-9ea5-1512e1cb2d2a)  
  
  
**Visibility Through Objects**  
To make the mesh visible through other objects, enable this option in the material settings:  
  
![SPT_10](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/a640201d-6d6a-47ce-9297-289032150479)
  
  
**Material Optimization**  
For convenience and versatility, translucent mode and the 2 sided option are enabled by default for all materials.   
If you don't need opacity, switch it to Opaque mode, this will have a positive effect on performance.   
  
![SPT_08](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/a9e39b28-ba08-48b4-879e-670fd5fa90b2)
  
  
If you never see the backside of polygons, disable the 2 Sided option, this will also improve performance.  
  
![SPT_09](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/950f9343-ea2b-4c3c-abd4-961b478897e8)
  
<br />  

## Features and Tips  
### Migrate  
You can migrate assets from the Example Project to your project as follows:  
1. Select the necessary assets.  
2. Select Migrate, all dependent assets that will also need to be migrated will be marked here. 
    
![SPT_18](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/b91ab1d3-5609-4a26-83ce-c1654b08bc47)
  
3. Select your project "Content" folder.  

### Disappearing Triangles   
If a triangles is not displayed, it is likely that you have two consecutive points that have the same or very close coordinates.  
You can fix this by using the Merge Border Points function, which finds and removes duplicate points.   

### Creation Static Mesh  
If necessary you can bake the DT Actor into a single mesh, this is a much more productive solution if you want to use DT as static object.

![Scr_05](https://github.com/AndrewEsenin/Dynamic_Triangulation_Documentation/assets/150374215/661a7dde-ca1a-4bf5-b543-e02100405896)

If, in addition to the procedural mesh, you use static meshes, after baking, you can once again merge everything together using Merge Actors (Window > Developer Tools).  

<br />

## Example Project  
Example Project (for UE versions 4.7 - 5.3)  
link  /**/   

BP_Demo_Helper contains all the logic for the runtime example.

Before you can open the Example Project you need to enable the plugin for your engine version ([read more](#Quick-Start)).   
You can migrate the entire level with examples or individual examples from Example Project to your project using migrate ([read more](#Migrate)). 
