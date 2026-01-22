# RiR_Draw
Toolbar focused on drafting work
For instructions on necessary installations see: [White Work](https://work.white.se/rhino-inside-revit/)  
General guides RiR: https://www.rhino3d.com/inside/revit/1.0/guides/  
Add the toolbar folder to your rhino.inside.revit tab according to this instruction (in the picture): https://discourse.mcneel.com/t/sharing-rhino-inside-scripts-among-team/131474/4 
or run the script with Grasshopper Player

## List of Scripts with short description

### Dimensioning
**00_Del_RiR** - Deletes dimensions and detail lines drawn by scripts below  
**01_Dim_Rooms** - Creates dimensions for rooms, detail lines are added to draw the dimensions between  
**02_Dim_Wall_Grid** - Creates dimensions from walls to nearest perpendicular grid  
**03_Dim_Cat_Center** - Creates dimensions for all objects of the selected object's category from center plane to closest wall  
**04_Dim_Cat_Side** - Creates dimensions for all objects of the selected object's category from side to closest wall  
**05_Dim_Type_Side** - Creates dimensions for all objects of the selected object's type from sides to closest walls  


### Marking
**20_QFilter** - Creates a filter that catches selected objects  
**21_LFilter** - Creates a filter that tries to catch all objects in a selected linked file  
**22_Filled Reg_Ele.gh** - Creates filled region covering selected elements  
**23_Iso_Sel_Cat.gh** - Creates and applies a view template that is a copy of the existing view template but with all categories exept of the selected objects hidden. Click again and the parent template is restored. 

### Commenting
**30_Hide_Red** - Hides all red text, lines or dimensions on a view or all views on a sheet  
**31_Show_Red.gh** - Show all red text, lines or dimensions on a view or all views on a sheet




# Script Documentation

## 10_Rev_Off Axis_Wall

**Intent:**  
To visualize and select walls with off axis direction

**Input:**  
An active viewport with visible gridlines

**Output:**  
Filled regions showing which walls that are off axis, These walls are also selected in the viewport.

**Dependencies:**  
Rhino  
Revit  
Rhino Inside Revit  

**Instructions:**
The script is best runned from the Revit Toolbar
1. While in a plan view with visible gridlines, click the script icon.
2. If walls are selected by the script, you might use **11_Ro_Wall_Off Axis** to rotate the walls.   
The script will select walls that are >1 degree of the direction of a gridline.
A new type of filled region is created which is deletable with **00_Del_RiR**

**Limitations/Known issues** 
If your model lacks filled regions or if theese are hidden in ypor active view they might not be visible.

**Linked scripts**
**10_Rev_Off Axis_Wall** can be used to rotate selected walls. **00_Del_RiR** can be used to delete filled regions in view.

**Contact:** 
Staffan Linné, staffan.linne@white.se


## 11_Ro_Wall_Off Axis

**Intent:**  
Rotate selected walls so they align with grids visible in view

**Input:**  
Views selected in the viewport.

**Output:**  
A rotation of the selected walls if they are off axis

**Dependencies:**  
Rhino  
Revit  
Rhino Inside Revit  

**Instructions:**
The script is best runned from the Revit Toolbar

1. Select an object (or several) in the Revit viewport  
2. Run script  
3. The script will rotate walls according to the gridline that has the most similar direction to the wall line direction  

**Limitations/Known issues** 
Long walls with hosted objects might delete some of these objects. Reason unknown. Might be resolved in the future.

**Linked scripts**
10_Rev_Off Axis_Wall can be used to reveal and select walls off axis 

**Contact:** 
Staffan Linné, staffan.linne@white.se




## 20_QFilter

**Intent:**  
To create a filter based on the Category, Type (Type Name), Family and Type Mark of an model object. 

**Input:**  
One or several selected model objects in the viewport

**Output:**  
A filter applied to the view or view template. To "save" the filter - rename it.

**Dependencies:**  
Rhino  
Revit  
Rhino Inside Revit  

**Instructions:**
The script is best runned from the Revit Toolbar

1. Select an object (or several) in the Revit viewport  
2. Run script  
3. The script will create a filter and apply a random colour to the filter  
4. If you like to keep the filter, change the name, otherwise it will be updated next time you use Qfilter

**Limitations/Known issues** 
Has been tested for linked models and works ok. Some linked object may be too poor in information to work properly.   
Does not work for certain object categories, for example views (section, elevations etc.) and annotation objects

**Linked scripts**
More complicated filter and legend for theese can be created by another script, available upon request

**Contact:** 
Staffan Linné, staffan.linne@white.se


## 21_LFilter

**Intent:**  
To create a filter based on the Category, Type (Type Name), Family and Type Mark of all objects in a linked file. 

**Input:**  
A selected linked model or an selected object in a linked file

**Output:**  
A filter applied to the view or view template. Filter is named after the linked file.
**Dependencies:**  
Rhino  
Revit  
Rhino Inside Revit  

**Instructions:**
The script is best runned from the Revit Toolbar

1. Select an object (or several) in the Revit viewport  
2. Run script  
3. The script will create a filter and apply a random colour to the filter  
4. If you like to keep the filter, change the name, otherwise it will be updated next time you use Qfilter

**Limitations/Known issues** 
Some linked object may be too poor in information to work properly. Object may also be marked in other linked files or in the active document, depending on how much information that is avaible for the linked objects. Works for revit linkes created from IFC files also.   
Does not work for certain object categories, for example views (section, elevations etc.) and annotation objects

**Linked scripts**
Qfilter (to just catch one or several linked objects)

**Contact:** 
Staffan Linné, staffan.linne@white.se





## 22_Filled Reg_Ele.gh

**Intent:**  
A quick way to create filled regions based on selected elements geometry

**Input:**  
One or several selected model objects in the viewport

**Output:**  
Filled regions covering the selected objects

**Dependencies:**  
Rhino  
Revit  
Rhino Inside Revit  

**Instructions:**
The script is best runned from the Revit Toolbar

1. Select an object (or several) in the Revit viewport  
2. Run script  
3. The script will create filled regions with the type named "Filled Region_RiR". 
4. If you want to keep the region, change type, if you want do delete it use **00_Del_RiR**

**Limitations/Known issues** 

**Linked scripts**  
**00_Del_RiR** can be used to delete filled regions in view.

**Contact:** 
Staffan Linné, staffan.linne@white.se
