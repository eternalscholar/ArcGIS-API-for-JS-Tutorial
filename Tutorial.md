**ArcGIS API for Javascript: An Introductory Tutorial**

**Introduction to ArcGIS API for Javascript**

The ArcGIS API for JavaScript is a powerful library that you can use to build applications that leverage the power of the ArcGIS Platform. One of the important feature that distinguishes this API from others is that it is designed to work with data items stored in the ArcGIS online platform. Beautiful visualizations of data, configuring pop-ups, and setting up bookmarks can be authored within the ArcGIS online platform without any coding, and these maps can be easily loaded into the app simply referencing the web map’s ID. Starting with the API 4.0 (launched in May 2016), one can follow the same pattern to create 3D web apps as well with ease. In ESRI terminology, the 2D Maps are called “Webmap” and 3D are called “Webscene”.

**Part I:  2D**

**Objective:** To add a point layer, a line layer and a polygon layer and overlay it on a basemap using ArcGIS API for Javascript. In exercise 1 of this tutorial, a point layer will be overlaid on a default basemap. The end product of exercise 1 will be an HTML file which when opened will show a point layer overlaid on a basemap. In exercise 2, we will create a new HTML file, add a point layer, a line layer and a polygon layer and change their styles. The end product will be an HTML file which when opened will show these three layers overlaid on a basemap.

**Data Used:**

Point Layer:- Trailheads near Los Angeles

Line Layer:- Trails with the trailheads

Polygon layer:- Parks and Openspaces near the trails

**Tools Required:**

Any Code editor 

**Exercise I: Add a point layer over a default** **background Map**

| Add background Map | Steps 1 and 2 |
| ------------------ | ------------- |
| Add Point Layer    | Steps 4 and 5 |

**Step 1. Create a blank HTML file**

Open notepad/code editor, save the file as Trailheads.html extension: 

**Step 2. Add the following Basic Template to the newly created HTML file.**

`<html>`

`<head>`

  <meta charset="utf-8">

  <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no">

  `<title>JavaScript Starter App</title>`

  <style>

​    `html, body, #viewDiv {`

​      `padding: 0;`

​      `margin: 0;`

​      `height: 100%;`

​      `width: 100%;`

​    `}`

  `</style>`

``  

  `<link rel="stylesheet" href="https://js.arcgis.com/4.10/esri/css/main.css">`

  <script src="https://js.arcgis.com/4.10/"></script>

``  

  <script>  

​    `require([`

​      `"esri/Map",`

​      `"esri/views/MapView"`

​    `], function(Map, MapView) {`

​      `var map = new Map({`

​        `basemap: "topo-vector"`

​      `});`

``      

​      `var view = new MapView({`

​        `container: "viewDiv",`

​        `map: map,`

​        `center: [-118.71511,34.09042],`

​        `zoom: 11`

​      `});`

``      

​    `});`

  `</script>`

`</head>`

`<body>`

  <div id="viewDiv"></div>

`</body>`

`</html>`

**Step 3. Open the HTML file in web browser. You should see a Map like the one below.****![img](https://lh3.googleusercontent.com/dOZGmjOOPQ7zUDaJ5EP-aYML8sXdXbf1KEETivu3q2Ree5q4Zkc3bQqNmjXCTngNsqutkmQkuXjBKE-RuYKLguAiafXi3bYCEMUY1vSGRS3eJFI0y2NZuTzWvu8HfEw8D_BkBRav)**

 

**Step 4. Replace the following 4 lines of code with the lines of code below it.**    

require([

​      "esri/Map",

​      "esri/views/MapView"

​    ], function(Map, MapView) {

**require****([**

  **"esri/Map"****,**

  **"esri/views/MapView"****,**

  **"esri/layers/FeatureLayer"**

**],** **function****(****Map, MapView, FeatureLayer****)** **{**

  **// Trailheads point feature layer**

  **var** **featureLayer =** **new** **FeatureLayer({**

​    **url:** **"https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Trailheads/FeatureServer"**

  **});**

**Step 5. Add the following single line of code immediately after the 3 lines of code shown below.**   

  **map.add(featureLayer);**

​     var map = new Map({

​       basemap: "topo-vector"

​     });

**Step 6: You should get something like this.** ![img](https://lh6.googleusercontent.com/k-xfG94eoxSI9KVko_ZfmK3J7d7TEe2hyWc-7irmQKqOJLIrCfVWMP2rz6bXZu8Em0KLCHT6iUqerQYNcW82VMRlXVfNhoJXRGCZn9xQmQWh3qIXam0cr7nqpW2G9uwVNvI8cBMB)

 

 

 

##  

 

 

 

 

 

**Exercise II: Styling the Feature Layers**

| **Synopsis:**                   | Add background Map                                           | Steps 1 and 2 |
| ------------------------------- | ------------------------------------------------------------ | ------------- |
| Add Point Layer and change icon | Steps 4 and 5                                                |               |
|                                 | Add Line layer (Trails) and change the color based on attribute “USE_BIKE”.USE_BIKE has values Yes or No. | Step 7        |
|                                 | Add Polygon layer () and change the color based on attribute “GIS_ACRES”.(Light pink: 0 to 1629 acres,Light green 1629 to 3754 acres, and Green 3754 to 11438 acres) | Step 9        |

**Step 1. Create a blank HTML file**

Open notepad, save file as Trails.html 

**Step 2. Add the following Basic Template to the newly created HTML file.**

<html>

<head>

  <meta charset="utf-8">

  <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no">

  <title>JavaScript Starter App</title>

  <style>

​    html, body, #viewDiv {

​      padding: 0;

​      margin: 0;

​      height: 100%;

​      width: 100%;

​    }

  </style>

  

  <link rel="stylesheet" href="https://js.arcgis.com/4.10/esri/css/main.css">

  <script src="https://js.arcgis.com/4.10/"></script>

  

  <script>  

​    require([

​      "esri/Map",

​      "esri/views/MapView"

​    ], function(Map, MapView) {

​      var map = new Map({

​        basemap: "topo-vector"

​      });

​      

​      var view = new MapView({

​        container: "viewDiv",

​        map: map,

​        center: [-118.71511,34.09042],

​        zoom: 11

​      });

​      

​    });

  </script>

</head>

<body>

  <div id="viewDiv"></div>

</body>

</html>

**Step 3. Open the HTML file in web browser. You should see a Map now.**

 

**Step 4. Replace the following 4 lines of code with the lines of code below it.**    

require([

​      "esri/Map",

​      "esri/views/MapView"

​    ], function(Map, MapView) {

require([

  "esri/Map",

  "esri/views/MapView",

  "esri/layers/FeatureLayer"

], function(Map, MapView, FeatureLayer) {

// Define a simple renderer and symbol

var trailheadsRenderer = {

  "type": "simple",

  "symbol": {

​    "type": "picture-marker",

​    "url": "http://static.arcgis.com/images/Symbols/NPS/npsPictograph_0231b.png",

​    "width": 10.5,

​    "height": 10.5

  }

}

 

// Create the layer and set the renderer

var trailheads = new FeatureLayer({

  url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Trailheads/FeatureServer/0",

  renderer: trailheadsRenderer

});

 

 

 

**Step 5. Add the following single line of code immediately after the 3 lines of code shown below.**   

  **map.add(trailheads);**

​     var map = new Map({

​       basemap: "topo-vector"

​     });

 

 

**Step 6. Open the HTML file in web browser to see the output.**

 ![img](https://lh5.googleusercontent.com/yOgwcOF5lAEDRh0lscOYZh4iWyq3boQ6AXy5GZaoj6gZaKhT9a8zwlQn-X4mECZm8euKkVZKAZvETshJdJtrAfdiuMYeRCKKKyCHRZ-p7WMfxZBxzWj0a566k8a_l_BppCFexEFr)

 

 

 

 

 

 

 

 

 

 

 

 

**Step 7.** ***Style the Trails layer by unique values***

**Paste the following code before the line of code “** var map = new Map({ **”**

 

// Define a unique value renderer and symbols

var trailsRenderer = {

  "type": "unique-value",

  "field": "USE_BIKE",

  "uniqueValueInfos": [

​    {

​      "value": "Yes",

​      "symbol": {

​        "color": [26, 26, 26, 255],

​        "width": 0.9,

​        "type": "simple-line",

​        "style": "dot"

​      },

​      "label": "Bikes"

​    },

​    {

​      "value": "No",

​      "symbol": {

​        "color": [230, 0, 0, 255],

​        "width": 0.9,

​        "type": "simple-line",

​        "style": "dot"

​      },

​      "label": "No Bikes"

​    }

  ]

}

 

// Create the layer and set the renderer

var trails = new FeatureLayer({

  url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Trails/FeatureServer/0",

  renderer: trailsRenderer

});

 

**Step 8. Add the following single line of code immediately after the 3 lines of code shown below.** 

**map.add(trails,0);**

 

​     var map = new Map({

​       basemap: "topo-vector"

​     });

 

**Step 8. Open the HTML file in web browser to see the output.**

 

 ![img](https://lh3.googleusercontent.com/3H4HDz8BcRfiPR-ZENxjLDoKjNSyVR7jbq_l2toSWD16FsCoLlQ8yXWZEm_3UrU_XI6g0S37t0yKmKFqC0YyKOhVQAzAZApPWQZGutj44u-9crK1THEGBCXp4eV7UV9A95pdpmnR)

 

 

 

 

 

 

 

 

 

 

 

 

**Step 9.** *Style the Parks and Open Spaces layer by numeric values*

**Paste the following code before the line of code “** var map = new Map({ **”**

 

  // Define a class breaks renderer and symbols

  var openSpacesRenderer = {

​    "type": "class-breaks",

​    "field": "GIS_ACRES",

​    "classBreakInfos": [

​      {

​        "symbol": {

​          "color": [

​            193,157,188,255

​          ],

​          "outline": {

​            "width": 0

​          },

​          "type": "simple-fill",

​          "style": "solid"

​        },

​        "label": "0 to 1,629",

​        "minValue": 0,

​        "maxValue": 1629

​      },

​      {

​        "symbol": {

​          "color": [

​            203,216,162,255

​          ],

​          "outline": {

​            "width": 0

​          },

​          "type": "simple-fill",

​          "style": "solid"

​        },

​        "label": "> 1,629 to 3,754",

​        "minValue": 1629,

​        "maxValue": 3754

​      },

​      {

​        "symbol": {

​          "color": [

​            144,198,120,255

​          ],

​          "outline": {

​            "width": 0

​          },

​          "type": "simple-fill",

​          "style": "solid"

​        },

​        "label": "> 3,754 to 11,438",

​        "minValue": 3754,

​        "maxValue": 11438

​      }

​    ]

  }

 

  // Create the layer and set the renderer

  var openspaces = new FeatureLayer({

​    url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Parks_and_Open_Space/FeatureServer/0",

​    renderer: openSpacesRenderer

  });

 

**Step 10. Add the following single line of code immediately after the 3 lines of code shown below.** 

**map.add(openspaces,0);**

 

​     var map = new Map({

​       basemap: "topo-vector"

​     });

 

 

**Step 11. Open the HTML file in web browser to see the output.**

 ![img](https://lh6.googleusercontent.com/lUVeEUiWH0bZyI4b9FeKMWeH-QYIWm-0K2Bi1P8VkzPceh3DRKaYzEZ2OJzWV8p7fF7_dv0TcSoTc8MEzNipGDtVFTDvzaVCV4Fu9EqYrqOH_lAcU63wZzKbqSZeqHuUFrYHdvxS)

 

 

 

 

 

 

**PART II: 3D**

 

 

 

**Objective:** **This sample demonstrates how to apply a size visual variable to extrude features thematically based on a numeric field value. We will be using a dataset that is hosted in ArcGIS online which contains the population of all the counties in USA and the number of people that live below the poverty line. In our 3D visualization, the color represents the percentage of people that live below the poverty level and size represents the number of people that lives below the poverty level.**

 

 

**Step 1: Create a new HTML file and name it 3D_Extrusion.html. Paste the following template code into it.**

 

**<!****DOCTYPE** **html****>**

**<****html****>**

 **<****head****>**

   <meta charset="utf-8" />

   **<****meta**

​     **name****=****"viewport"**

​     **content****=****"initial-scale=1,maximum-scale=1,user-scalable=no"**

   **/>**

   **<****title****>****Data-driven extrusion - 4.11****</****title****>**

 

   **<****link**

​     **rel****=****"stylesheet"**

​     **href****=****"https://js.arcgis.com/4.11/esri/themes/light/main.css"**

   **/>**

   <script src="https://js.arcgis.com/4.11/"></script>

   <style>

​       **html****,**

​       **body****,**

​       **#viewDiv** **{**

​         **padding****:** **0****;**

​         **margin****:** **0****;**

​         **height****:** **100%****;**

​         **width****:** **100%****;**

​       **}**

​     **</****style****>**

      <script>

​       **require****([**

​         **"esri/Map"****,**

​         **"esri/views/SceneView"****,**

​         **"esri/layers/FeatureLayer"****,**

​         **"esri/widgets/Legend"**

​       **],** **function****(****Map****,** **SceneView****,** **FeatureLayer****,** **Legend****) {**

​         **var** **map** **=** **new** **Map****({**

​         **basemap:** **"gray"****,**

​       **});**

​       **var** **view** **=** **new** **SceneView****({**

​         **container:** **"viewDiv"****,**

​         **map:** **map****,**

​         **viewingMode:** **"local"****,**

​         **camera:** **{**

​           **position:** **{**

​             **latitude:** **18.24237****,**

​             **longitude:** **-****88.72943****,**

​             **z:** **1534560**

​           **},**

​           **tilt:** **45****,**

​           **heading:** **10**

​         **}**

​       **});**

   **});**

   **</****script****>**

 **</****head****>**

 

 **<****body****>**

   <div id="viewDiv"></div>

 **</****body****>**

**</****html****>**

 

**Step 2: Save the file and open it. It should look like this.**

 

 ![img](https://lh4.googleusercontent.com/w9Ox1M4-T714T5KE3tI-b4Wb9HTrh6sPP8agL_dWbMe6R1MbVwM_7_3hjAKjZrOBOM1nME3A5dTZnmDJjgZ9V1LAZkxtamAC3qKJl4RmCh5zI1PZbeYKueBGAx-SW8nKSiBieSSg)

**Step 3: Paste the following code before  “****var** **map** **=** **new** **Map****({****”**

 

**// Newly added code starts here**

​       **var** **renderer** **= {**

​         **type:** **"simple"****,** **// autocasts as new SimpleRenderer()**

​         **symbol:** **{**

​           **type:** **"polygon-3d"****,** **// autocasts as new PolygonSymbol3D()**

​           **symbolLayers:** **[**

​             **{**

​               **type:** **"extrude"** **// autocasts as new ExtrudeSymbol3DLayer()**

​             **}**

​           **]**

​         **},**

​         **visualVariables:** **[**

​           **{**

​             **type:** **"size"****,**

​             **field:** **"POP_POVERTY"****,**

​             **stops:** **[**

​               **{**

​                 **value:** **1000****,**

​                 **size:** **10000****,**

​                 **label:** **"1,000"**

​               **},**

​               **{**

​                 **value:** **150000****,**

​                 **size:** **300000****,**

​                 **label:** **">150,000"**

​               **}**

​             **]**

​           **},**

​           **{**

​             **type:** **"color"****,**

​             **field:** **"POP_POVERTY"****,**

​             **normalizationField:** **"TOTPOP_CY"****,**

​             **legendOptions:** **{**

​               **title:** **"% population with income below poverty level"**

​             **},**

​             **stops:** **[**

​               **{**

​                 **value:** **0.1****,**

​                 **color:** **"#FFFCD4"****,**

​                 **label:** **"<15%"**

​               **},**

​               **{**

​                 **value:** **0.35****,**

​                 **color:** **[****153****,** **83****,** **41****],**

​                 **label:** **">35%"**

​               **}**

​             **]**

​           **}**

​         **]**

​       **};**

 

 

​       **var** **povLayer** **=** **new** **FeatureLayer****({**

​         **url:**

​           **"https://services.arcgis.com/V6ZHFr6zdgNZuVG0/arcgis/rest/services/counties_politics_poverty/FeatureServer/0"****,**

​         **renderer:** **renderer****,**

​         **title:** **"Population living in poverty by county"****,**

​         **outFields:** **[****"\*"****]**

​       **});**

 

**// Newly added code ends here**

 

**Step 4:** **Add the following single line of code immediately after the 2 lines of code shown below.** 

**layers: [povLayer]**

 

**var map = new Map({**

​         **basemap: "gray",**

 

**Step 5: Save the file and open it. You should see something like this.**

 

 

 ![img](https://lh3.googleusercontent.com/ijti0zxFyVxn9APrNtMCyTdZZQKoPu-IVV5MyVgiVbQAfMoSFMV-_QEmDsJ6_M8WlUmMQXQAvNJ0cYLJzwDJVPYCFOa1Gj4rA8Y1fSdii-a3-BGsGFamsjtCzLN5F7_4PFAIbGEI)

 

 

**Step 6:** 

 

 

 

 