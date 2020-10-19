<template>
  <div id="app" class="h-100">
    <baidu-map
      class="BaiduMap"
      :center="center"
      :zoom="zoom"
      @ready="mapInit"
    >
      <bm-navigation anchor="BMAP_ANCHOR_TOP_RIGHT" ref="navbar01"></bm-navigation>
      <bml-marker-clusterer :averageCenter="true" ref="clusterRef">
        <bm-marker
          v-for="(marker,index) in markers"
          :key="index"
          :position="{lng: marker.lng, lat: marker.lat}"
          :offset="{width: 0,height: -15}"
        />
      </bml-marker-clusterer>
    </baidu-map>
  </div>
</template>

<script type="text/javascript" src="./js/bmap.js"></script>
<script>
import Vue from 'vue'
import BaiduMap from 'vue-baidu-map'
import BmlMarkerClusterer from './components/MarkerCluster'

Vue.use(BaiduMap, {
  ak: 'fVwxO2FtvgezfQtWzqdHaoGb'
})
export default {
  name: 'App',
  data () {
    return {
      bmap: '',
      center: { lng: 0, lat: 0 },
      zoom: 5,
      markers: []
    }
  },
  components: {
    BmlMarkerClusterer
  },
  mounted () {
    window.addEventListener('message', function (e) {
      if (e.data.type === 'baludCluster') {
        alert(e.data.value)
      }
    })
  },
  methods: {
    mapInit (map) {
      this.center.lng = 121.234
      this.center.lat = 25.055
      this.zoom = 3
      this.bmap = map

      for (let i=0 ;i<10; i++) {
        this.markers.push({lng: Math.random() * 20 + 85, lat: Math.random() * 10 + 21})
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.BaiduMap {
  height: 500px;
}
</style>
