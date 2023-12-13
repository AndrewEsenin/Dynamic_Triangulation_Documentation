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
If you want to use Path Tracer at runtime, you can do the following:
Create a new Path Tracer using the Spawn Actor from Class function, selecting one of the ready-made examples, and connect this node to the Begin Play event (for example in Player Controller).  

![SPT_20](https://github.com/AndrewEsenin/Simple_Path_Tracer_Documentation/assets/150374215/9192f9dc-d16d-4781-a9d2-f3fa75a39bed)
