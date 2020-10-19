# baidu-marker-cluster

## Project setup
```
npm install deviceon-baidumap-marker-cluster
```

## How to use
```
import BmlMarkerClusterer from 'deviceon-baidumap-marker-cluster'

Vue.use(BmlMarkerClusterer)

<bml-marker-clusterer :averageCenter="true">
</bml-marker-clusterer>

window.addEventListener('message', function (e) {
  if (e.data.type === 'baludCluster') {
    if (e.data.value !== 'mouseout') {
      // mouseover action
      // e.data.value = {
        //cluster center location
        lat: 0,
        lng: 0,
        //markers location which under cluster
        markers: [{
          lat: 0,
          lng: 0
        },{...}]
      }
    } else {
      // mouseout action
      // e.data.value === 'mouseout
    }
  }
})
```
