<template>
<div class="all-content">

  <div id="mapid">
    <img alt="leaflet map" >
    <mapid  ></mapid>
  </div>

</div>
</template>

<script>
import MapDisplay from './components/map.vue'

export default {
  name: 'app',
  data(){
    return {
      location: {},
      iss_position: {}
    };
  },
  components: {
  'mapid':  MapDisplay
},
computed: {
  currentLatitude(){
  return this.iss_position.latitude;

},
currentLongitude(){
  return this.iss_position.longitude;
}
},
mounted(){
  fetch('http://api.open-notify.org/iss-now.json')
   .then(res => res.json())
   .then(data => {
     this.iss_position = data.iss_position;
     console.log(this.iss_position);
     console.log(this.iss_position.latitude);
  }
)
},
methods:{

}
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#mapid { height: 180px; }
</style>

<!-- function moveISS () {
    $.getJSON('http://api.open-notify.org/iss-now.json?callback=?', function(data) {
        var lat = data['iss_position']['latitude'];
        var lon = data['iss_position']['longitude'];

        // See leaflet docs for setting up icons and map layers
        // The update to the map is done here:
        iss.setLatLng([lat, lon]);
        isscirc.setLatLng([lat, lon]);
        map.panTo([lat, lon], animate=true);
    });
    setTimeout(moveISS, 5000);
} -->
