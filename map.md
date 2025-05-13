---
title: Mapa de Riesgo Sísmico en Perú
nav_order: 3
---

# Mapa Interactivo con Capa .tif (Perú)

Este mapa muestra la capa de riesgo sísmico en Perú con un archivo .tif. La capa tiene una opacidad de 0.8 y usa el colormap **Jet**.

<div id="map" style="height: 500px;"></div>

<script>
  // Crear el mapa centrado en Perú (coordenadas aproximadas)
  var map = L.map('map').setView([-9.19, -75.0152], 6);  // Coordenadas para Perú
  
  // Mapa base de OpenStreetMap
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png').addTo(map);

  // Agregar la capa .tif (Imagen de ejemplo convertida a PNG en la URL)
  var tifLayer = L.imageOverlay('https://yourdomain.com/path/to/your/tif/image.png', [
    [-18.0, -81.0],  // Coordenadas SW del área de la capa
    [-0.5, -68.0]    // Coordenadas NE del área de la capa
  ], {
    opacity: 0.8,  // Opacidad de la capa
    attribution: 'Datos de ejemplo'
  }).addTo(map);

  // Agregar una barra de color (usando colormap Jet)
  var legend = L.control({position: 'bottomright'});
  legend.onAdd = function(map) {
    var div = L.DomUtil.create('div', 'info legend');
    var grades = [0, 1, 2, 3, 4];  // Definir los valores de la leyenda
    var labels = [];
    
    // Crear una barra de leyenda usando colormap Jet (simulado)
    for (var i = 0; i < grades.length; i++) {
      div.innerHTML += '<i style="background:' + getJetColor(grades[i]) + '"></i> ' + grades[i] + '<br>';
    }
    return div;
  };
  legend.addTo(map);

  // Función para asignar color usando Jet colormap
  function getJetColor(value) {
    var colors = [
      '#0000FF', '#00FFFF', '#00FF00', '#FFFF00', '#FF0000'  // Colores simulados Jet
    ];
    return colors[value];
  }
</script>
