# ArcGIS API for Javascript: An Introductory Tutorial



## Tutorial I:  Visualizing in 2D

**Objective:** To add a point layer, a line layer and a polygon layer and overlay it on a basemap using ArcGIS API for Javascript. In exercise 1 of this tutorial, a point layer will be overlaid on a default basemap. The end product of exercise 1 will be an HTML file which when opened will show a point layer overlaid on a basemap. In exercise 2, we will create a new HTML file, add a point layer, a line layer and a polygon layer and change their styles. The end product will be an HTML file which when opened will show these three layers overlaid on a basemap.

**Data Used:**

All the data required for this tutorial is available online and no downloads are required. We will be using three layers in our 2D tutorial which are available from ArcGIS online.

Point Layer:- Trailheads near Los Angeles,  
Line Layer:- Trails with the trailheads,  
Polygon layer:- Parks and Openspaces near the trails

**Tools Required:**

None. You may use [codepen.io](https://codepen.io/) as an online HTML code editor.

---



### Exercise I: Add a point layer over a default background Map

| **Synopsis:**      |               |
| ------------------ | ------------- |
| Add background Map | Steps 1 and 2 |
| Add Point Layer    | Steps 4 and 5 |

**Step 1. Create a blank HTML file**

Open [codepen.io](https://codepen.io/)  

**Step 2. Add the following Basic Template to the HTML section in codepen.**

``` html
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no">
  <title>JavaScript Starter App</title>
  <style>
    html, body, #viewDiv {
      padding: 0;
      margin: 0;
      height: 100%;
      width: 100%;
    }
  </style>
  
  <link rel="stylesheet" href="https://js.arcgis.com/4.10/esri/css/main.css">
  <script src="https://js.arcgis.com/4.10/"></script>
  
  <script>  
    require([
      "esri/Map",
      "esri/views/MapView"
    ], function(Map, MapView) {

      var map = new Map({
        basemap: "topo-vector"
      });
      
      var view = new MapView({
        container: "viewDiv",
        map: map,
        center: [-118.71511,34.09042],
        zoom: 11
      });
      
    });
  </script>
</head>
<body>
  <div id="viewDiv"></div>
</body>
</html>

```





**Step 3. You should see a Map like the one below.**![img](https://lh3.googleusercontent.com/dOZGmjOOPQ7zUDaJ5EP-aYML8sXdXbf1KEETivu3q2Ree5q4Zkc3bQqNmjXCTngNsqutkmQkuXjBKE-RuYKLguAiafXi3bYCEMUY1vSGRS3eJFI0y2NZuTzWvu8HfEw8D_BkBRav)

 

**Step 4. ***Create a reference to the point layer (trailheads)***
**Replace the following 4 lines of code (lines 19-22) with the lines of code below it.**

```javascript
require([
      "esri/Map",
      "esri/views/MapView"
    ], function(Map, MapView) {

```

```javascript
require([
  "esri/Map",
  "esri/views/MapView",
  "esri/layers/FeatureLayer"
], function(Map, MapView, FeatureLayer) {
  // Trailheads point feature layer
  var featureLayer = new FeatureLayer({
    url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Trailheads/FeatureServer"
  });

```



**Step 5. ***Add the point layer(trailheads) to the map***
**Add the following single line of code immediately after the 3 lines of code shown below (lines 28-30. This may vary if you have extra blank lines).**   

```javascript
map.add(featureLayer);
```

```javascript
var map = new Map({
    basemap: "topo-vector"
});

```



**Step 6: You should get something like this.** ![img](https://lh6.googleusercontent.com/k-xfG94eoxSI9KVko_ZfmK3J7d7TEe2hyWc-7irmQKqOJLIrCfVWMP2rz6bXZu8Em0KLCHT6iUqerQYNcW82VMRlXVfNhoJXRGCZn9xQmQWh3qIXam0cr7nqpW2G9uwVNvI8cBMB)

 

 

##  



 

### Exercise II: Styling the Feature Layers 

| **Synopsis**                                                 |               |
| ------------------------------------------------------------ | ------------- |
| Add background Map                                           | Steps 1 and 2 |
| Add Point Layer and change icon                              | Steps 4 and 5 |
| Add Line layer (Trails) and change the color based on attribute<br />  “USE_BIKE”. USE_BIKE has values Yes or No. | Step 7        |
| Add Polygon layer (parks and open space) and change the color based on<br> attribute “GIS_ACRES”.(Light pink: 0 to 1629 acres,Light green 1629 to 3754<br> acres, and Green 3754 to 11438 acres) | Step 9        |

**Step 1. Create a blank HTML file**

Open [codepen.io](https://codepen.io/) 

**Step 2. Add the following Basic Template to the HTML section in codepen.io.**

```html
<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no">
  <title>JavaScript Starter App</title>
  <style>
    html, body, #viewDiv {
      padding: 0;
      margin: 0;
      height: 100%;
      width: 100%;
    }
  </style>
  
  <link rel="stylesheet" href="https://js.arcgis.com/4.10/esri/css/main.css">
  <script src="https://js.arcgis.com/4.10/"></script>
  
  <script>  
    require([
      "esri/Map",
      "esri/views/MapView"
    ], function(Map, MapView) {

      var map = new Map({
        basemap: "topo-vector"
      });
      
      var view = new MapView({
        container: "viewDiv",
        map: map,
        center: [-118.71511,34.09042],
        zoom: 11
      });
      
    });
  </script>
</head>
<body>
  <div id="viewDiv"></div>
</body>
</html>

```



**Step 3. You should see a Map now.**

 ![img](https://lh5.googleusercontent.com/nHSJwW-YNqi5At0F5hSdSImxkAls4NyOL50cJ5mo8xXEj3Xqxx0oee5Xb0xc0KNUpHt7lv4kD_XX_Emww1eshO4wIbh7zJa4JVcp6BppapM-x-1o6prYXdX75GcipdGhqJubaSta)



**Step 4. Replace the following 4 lines of code (lines 19-22) with the lines of code below it.**    

```javascript
require([
      "esri/Map",
      "esri/views/MapView"
    ], function(Map, MapView) {
```

```javascript
require([
  "esri/Map",
  "esri/views/MapView",
  "esri/layers/FeatureLayer"
], function(Map, MapView, FeatureLayer) {
// Define a simple renderer and symbol
var trailheadsRenderer = {
  "type": "simple",
  "symbol": {
    "type": "picture-marker",
    "url": "http://static.arcgis.com/images/Symbols/NPS/npsPictograph_0231b.png",
    "width": 10.5,
    "height": 10.5
  }
}
 
// Create the layer and set the renderer
var trailheads = new FeatureLayer({
  url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Trailheads/FeatureServer/0",
  renderer: trailheadsRenderer
});

```



**Step 5. Add the following single line of code immediately after the 3 lines of code (lines 41-43, more or less) shown below.**   

  ```javascript
map.add(trailheads);
  ```

```javascript
var map = new Map({
    basemap: "topo-vector"
});
```



**Step 6. You should be seeing something like this.**

 ![img](https://lh5.googleusercontent.com/yOgwcOF5lAEDRh0lscOYZh4iWyq3boQ6AXy5GZaoj6gZaKhT9a8zwlQn-X4mECZm8euKkVZKAZvETshJdJtrAfdiuMYeRCKKKyCHRZ-p7WMfxZBxzWj0a566k8a_l_BppCFexEFr)

 

  

**Step 7.** ***Style the Trails layer by unique values***

**Paste the code snippet down below before the following line of code (line 41, more or less)**  

 ```javascript
var map = new Map({
 ```

```javascript
// Define a unique value renderer and symbols
var trailsRenderer = {
  "type": "unique-value",
  "field": "USE_BIKE",
  "uniqueValueInfos": [
    {
      "value": "Yes",
      "symbol": {
        "color": [26, 26, 26, 255],
        "width": 0.9,
        "type": "simple-line",
        "style": "dot"
      },
      "label": "Bikes"
    },
    {
      "value": "No",
      "symbol": {
        "color": [230, 0, 0, 255],
        "width": 0.9,
        "type": "simple-line",
        "style": "dot"
      },
      "label": "No Bikes"
    }
  ]
}
 
// Create the layer and set the renderer
var trails = new FeatureLayer({
  url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Trails/FeatureServer/0",
  renderer: trailsRenderer
});
```



 **Step 8. Add the following single line of code immediately after the 2 lines of code shown below (lines 74-75, more or less).** 

```javascript
map.add(trails,0);
```

```javascript
    basemap: "topo-vector"
});
```



**Step 8. You should be seeing something like this.**

  ![img](https://lh3.googleusercontent.com/3H4HDz8BcRfiPR-ZENxjLDoKjNSyVR7jbq_l2toSWD16FsCoLlQ8yXWZEm_3UrU_XI6g0S37t0yKmKFqC0YyKOhVQAzAZApPWQZGutj44u-9crK1THEGBCXp4eV7UV9A95pdpmnR)

 

 

**Step 9. Style the Parks and Open Spaces layer by numeric values**

Paste the code snippet down below before the following line of code (line 73, more or less)

 ```javascript
var map = new Map({
 ```

```javascript
// Define a class breaks renderer and symbols
  var openSpacesRenderer = {
    "type": "class-breaks",
    "field": "GIS_ACRES",
    "classBreakInfos": [
      {
        "symbol": {
          "color": [
            193,157,188,255
          ],
          "outline": {
            "width": 0
          },
          "type": "simple-fill",
          "style": "solid"
        },
        "label": "0 to 1,629",
        "minValue": 0,
        "maxValue": 1629
      },
      {
        "symbol": {
          "color": [
            203,216,162,255
          ],
          "outline": {
            "width": 0
          },
          "type": "simple-fill",
          "style": "solid"
        },
        "label": "> 1,629 to 3,754",
        "minValue": 1629,
        "maxValue": 3754
      },
      {
        "symbol": {
          "color": [
            144,198,120,255
          ],
          "outline": {
            "width": 0
          },
          "type": "simple-fill",
          "style": "solid"
        },
        "label": "> 3,754 to 11,438",
        "minValue": 3754,
        "maxValue": 11438
      }
    ]
  }
 
  // Create the layer and set the renderer
  var openspaces = new FeatureLayer({
    url: "https://services3.arcgis.com/GVgbJbqm8hXASVYi/arcgis/rest/services/Parks_and_Open_Space/FeatureServer/0",
    renderer: openSpacesRenderer
  });
```



**Step 10. Add the following single line of code immediately after the 2 lines of code (lines 132-133, more or less) shown below.** 

```javascript
map.add(openspaces,0);
```

```javascript
    basemap: "topo-vector"
});
```

 

**Step 11. Your final output should be like this.**

 ![img](https://lh6.googleusercontent.com/lUVeEUiWH0bZyI4b9FeKMWeH-QYIWm-0K2Bi1P8VkzPceh3DRKaYzEZ2OJzWV8p7fF7_dv0TcSoTc8MEzNipGDtVFTDvzaVCV4Fu9EqYrqOH_lAcU63wZzKbqSZeqHuUFrYHdvxS)

 

 

