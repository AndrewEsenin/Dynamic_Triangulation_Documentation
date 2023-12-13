# Dynamic_Triangulation_Documentation

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

Before you can open the Example Project you need to enable the plugin for your engine version ([read more](#Quick-Start)).   
You can migrate the entire level with examples or individual examples from Example Project to your project using migrate ([read more](#Migrate)). 
