<!DOCTYPE html>
<html>
  <head>
  <style>
    #map-canvas { width:500px; height:400px; }
    .layer-wizard-search-label { font-family: sans-serif };
  </style>
  <script type="text/javascript"
    src="http://maps.google.com/maps/api/js?sensor=false">
  </script>
  <script type="text/javascript">
    var map;
    var layer_0;
    var layer_1;
    function initialize() {
      map = new google.maps.Map(document.getElementById('map-canvas'), {
        center: new google.maps.LatLng(39.28804562429281, -76.62750445),
        zoom: 14,
        mapTypeId: google.maps.MapTypeId.ROADMAP
      });
      layer_0 = new google.maps.FusionTablesLayer({
        query: {
          select: "col8",
          from: "1gPUiaDyfgLJlWpoYV8d0P-5pjY46icwX6dTcXd9J"
        },
        map: map,
        styleId: 2,
        templateId: 2
      });
      layer_1 = new google.maps.FusionTablesLayer({
        query: {
          select: "col3",
          from: "1R8nfaoLKAaonhISSxKKJvel3zoFLllkmWCNSwJoM"
        },
        map: map,
        styleId: 2,
        templateId: 2
      });
    }
    function changeMap_1() {
      var whereClause;
      var searchString = document.getElementById('search-string_1').value.replace(/'/g, "\\'");
      if (searchString != '--Select--') {
        whereClause = "'Category' = '" + searchString + "'";
      }
      layer_1.setOptions({
        query: {
          select: "col3",
          from: "1R8nfaoLKAaonhISSxKKJvel3zoFLllkmWCNSwJoM",
          where: whereClause
        }
      });
    }
    google.maps.event.addDomListener(window, 'load', initialize);
  </script>
  </head>
  <body>
    <div id="map-canvas"></div>
    <div style="margin-top: 10px;">
      <label class="layer-wizard-search-label">
        Category
        <select id="search-string_1" onchange="changeMap_1(this.value);">
          <option value="--Select--">--Select--</option>
          <option value="Education">Education</option>
          <option value="Health Facilities/Services">Health Facilities/Services</option>
          <option value="Lifestyle">Lifestyle</option>
          <option value="Nutrition">Nutrition</option>
        </select>
      </label> 
    </div>
  </body>
</html>
