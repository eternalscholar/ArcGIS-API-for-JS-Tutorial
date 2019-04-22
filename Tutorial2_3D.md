## Tutorial II:  Visualizing in 3D



**Objective:** This sample demonstrates how to apply a size visual variable to extrude features thematically based on a numeric field value. We will be using a dataset that is hosted in ArcGIS online which contains the population of all the counties in USA and the number of people that live below the poverty line. In our 3D visualization, the color represents the percentage of people that live below the poverty level and size represents the number of people that lives below the poverty level.

  

**Step 1: Paste the following template code into [codepen.io](https://codepen.io/).**

 ```html
<!DOCTYPE html>
<html>
 <head>
   <meta charset="utf-8" />
   <meta
     name="viewport"
     content="initial-scale=1,maximum-scale=1,user-scalable=no"
   />
   <title>Data-driven extrusion - 4.11</title>
 
   <link
     rel="stylesheet"
     href="https://js.arcgis.com/4.11/esri/themes/light/main.css"
   />
   <script src="https://js.arcgis.com/4.11/"></script>
   <style>
       html,
       body,
       #viewDiv {
         padding: 0;
         margin: 0;
         height: 100%;
         width: 100%;
       }
     </style>
      <script>
       require([
         "esri/Map",
         "esri/views/SceneView",
         "esri/layers/FeatureLayer",
         "esri/widgets/Legend"
       ], function(Map, SceneView, FeatureLayer, Legend) {
         var map = new Map({
         basemap: "gray",
       });
       var view = new SceneView({
         container: "viewDiv",
         map: map,
         viewingMode: "local",
         camera: {
           position: {
             latitude: 18.24237,
             longitude: -88.72943,
             z: 1534560
           },
           tilt: 45,
           heading: 10
         }
       });
   });
   </script>
 </head>
 
 <body>
   <div id="viewDiv"></div>
 </body>
</html>
 ```





**Step 2: You should get something like this.**

  ![img](https://lh4.googleusercontent.com/w9Ox1M4-T714T5KE3tI-b4Wb9HTrh6sPP8agL_dWbMe6R1MbVwM_7_3hjAKjZrOBOM1nME3A5dTZnmDJjgZ9V1LAZkxtamAC3qKJl4RmCh5zI1PZbeYKueBGAx-SW8nKSiBieSSg)



**Step 3: Paste the code snippet below before the following single line of code**

 ```javascript
var map = new Map({
 ```

```javascript
var renderer = {
         type: "simple", // autocasts as new SimpleRenderer()
         symbol: {
           type: "polygon-3d", // autocasts as new PolygonSymbol3D()
           symbolLayers: [
             {
               type: "extrude" // autocasts as new ExtrudeSymbol3DLayer()
             }
           ]
         },
         visualVariables: [
           {
             type: "size",
             field: "POP_POVERTY",
             stops: [
               {
                 value: 1000,
                 size: 10000,
                 label: "1,000"
               },
               {
                 value: 150000,
                 size: 300000,
                 label: ">150,000"
               }
             ]
           },
           {
             type: "color",
             field: "POP_POVERTY",
             normalizationField: "TOTPOP_CY",
             legendOptions: {
               title: "% population with income below poverty level"
             },
             stops: [
               {
                 value: 0.1,
                 color: "#FFFCD4",
                 label: "<15%"
               },
               {
                 value: 0.35,
                 color: [153, 83, 41],
                 label: ">35%"
               }
             ]
           }
         ]
       };
 
 
       var povLayer = new FeatureLayer({
         url:
           "https://services.arcgis.com/V6ZHFr6zdgNZuVG0/arcgis/rest/services/counties_politics_poverty/FeatureServer/0",
         renderer: renderer,
         title: "Population living in poverty by county",
         outFields: ["*"]
       });
```





**Step 4: You should see something like this.**  ![img](https://lh3.googleusercontent.com/ijti0zxFyVxn9APrNtMCyTdZZQKoPu-IVV5MyVgiVbQAfMoSFMV-_QEmDsJ6_M8WlUmMQXQAvNJ0cYLJzwDJVPYCFOa1Gj4rA8Y1fSdii-a3-BGsGFamsjtCzLN5F7_4PFAIbGEI)

 

 **Step 5:** *Include Pop-up*

**Replace the following single line of code by the code snippet below**

```javascript
outFields: ["*"]
```

```javascript
outFields: ["*"],
         popupTemplate: {
           // autocasts as new PopupTemplate()
           title: "{COUNTY}, {STATE}",
           content:
             "{POP_POVERTY} of {TOTPOP_CY} people live below the poverty line.",
           fieldInfos: [
             {
               fieldName: "POP_POVERTY",
               format: {
                 digitSeparator: true,
                 places: 0
               }
             },
             {
               fieldName: "TOTPOP_CY",
               format: {
                 digitSeparator: true,
                 places: 0
               }
             }
           ]
         }
```



​        

**Step 6: You should see something like this.** ![img](https://lh6.googleusercontent.com/RYuJD6VXktwfBm7Ln4lDD_NeHyF6_22LoWDQG5CgmCEZNPjeDu7wsqel_7r_l0XoR8yLZK6tEzC8Y1EBIH0w_nQCxmOhU4-RIlTiOx111Ntq33YaJYf7U0qbU5UN69i8Gu3du_WS)

 

 

**Step 7: Include Legend**

**Replace the following three lines of code (at the bottom) with the code snippet below.** 

```javascript
       });
   </script>
 </head>
```



 ```javascript
       var legend = new Legend({
         view: view
       });
 
       view.ui.add(legend, "bottom-right");
       });
   </script>
 </head>
 ```



 

 **Step 8: Your final output should look like this.** ![img](https://lh5.googleusercontent.com/v7Ylor1gm-P8E_TOcWz8_p2UwkcPAd9xdLtm21Pmta2D6ygz3Z5daPJ2iJ-Kx1IciJit0I99ywcLgx1VbjJKBu6AW65DqyWBBdxAKjRchDD7_6mYulsOxm88pzmYT4YP55q9_s4C)



