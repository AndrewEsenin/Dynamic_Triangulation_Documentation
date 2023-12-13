# Dynamic Triangulation Documentation

Unreal Marketplace Link:   
YouTube:  
Support email: andrewesenin27@gmail.com  
Example Project:  
Playble Demo:  
  
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


You can download the [Example Project](#Example-Project), it contains many additional examples.  

<br />

## Quick Start  
1. Install the plugin on your version of the engine.    

![SPT_01](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/f9ae88e2-fff4-47d3-abbf-eb3cb51c0896)


2. Activate the plugin (if not activated) and restart the engine.

![SPT_38](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/058ea1ff-efce-46ca-974b-7182587adee2)


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
To make the path visible through other objects, enable this option in the material settings:  
  
![SPT_10](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/a640201d-6d6a-47ce-9297-289032150479)
  
  
**Material Optimization**  
For convenience and versatility, translucent mode and the 2 sided option are enabled by default for all materials.   
If you don't need opacity, switch it to Opaque mode, this will have a positive effect on performance.   
  
![SPT_08](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/a9e39b28-ba08-48b4-879e-670fd5fa90b2)
  
  
If you never see the backside of path polygons, disable the 2 Sided option, this will also improve performance.  
  
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
Example Project (for UE versions 4.6 - 5.3)  
link  /**/   

BP_Demo_Helper contains all the logic for the runtime example.

Before you can open the Example Project you need to enable the plugin for your engine version ([read more](#Quick-Start)).   
You can migrate the entire level with examples or individual examples from Example Project to your project using migrate ([read more](#Migrate)). 
