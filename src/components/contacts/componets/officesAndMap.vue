<template>
  <section class="contacts__section offices-and-map">
    <div class="container">
      <div class="contacts__row">
        <article class="our-offices">
          <div class="container">
            <header class="our-offices-title">
              <h3 class="title-h3">Our Offices</h3>
            </header>
            <div class="contacts__tabs tabs">
              <ul class="contacts__tabs-titles tabs__titles">
                <li class="tabs__title"
                    v-for="tab in tabs"
                    :key="tab.nameCity"
                    :class="{active: currentTab.nameCity === tab.nameCity}"
                    @click="currentTab = tab">{{tab.nameCity}}
                </li>
              </ul>
              <div class="tabs__description">
                <div class="tabs__place">
                  <p>{{currentTab.place}}</p>
                </div>
                <div class="tabs__address">
                  <p>{{currentTab.address}}
                  </p>
                </div>
              </div>
            </div>
          </div>
        </article>
      </div>
    </div>
    <div class="contacts__map">
      <GmapMap
        :center="currentMarker"
        :zoom="11"
        map-type-id="terrain"
        style="width: 100%; height: 100%"
        :options="mapStyle"
      >
        <GmapCircle
          :center="currentMarker"
          :radius="1000"
          :visible="true"
          :options="{fillColor:'#3db565',fillOpacity: 1.0}"
        ></GmapCircle>
      </GmapMap>
    </div>
  </section>
</template>
<script>
export default {
  name: 'map',
  props: {
    tabs: Array,
    markers: Object
  },
  data () {
    return {
      tabs: this.tabs,
      currentTab: this.tabs[0],
      markers: this.markers,
      currentMarker: null,
      mapStyle: {
        zoomControl: false,
        mapTypeControl: false,
        streetViewControl: false,
        fullscreenControl: false,
        styles: [
          {
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#212121'
              }
            ]
          },
          {
            'elementType': 'labels.icon',
            'stylers': [
              {
                'visibility': 'off'
              }
            ]
          },
          {
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#757575'
              }
            ]
          },
          {
            'elementType': 'labels.text.stroke',
            'stylers': [
              {
                'color': '#212121'
              }
            ]
          },
          {
            'featureType': 'administrative',
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#757575'
              }
            ]
          },
          {
            'featureType': 'administrative.country',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#9e9e9e'
              }
            ]
          },
          {
            'featureType': 'administrative.land_parcel',
            'stylers': [
              {
                'visibility': 'off'
              }
            ]
          },
          {
            'featureType': 'administrative.locality',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#bdbdbd'
              }
            ]
          },
          {
            'featureType': 'poi',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#757575'
              }
            ]
          },
          {
            'featureType': 'poi.park',
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#181818'
              }
            ]
          },
          {
            'featureType': 'poi.park',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#616161'
              }
            ]
          },
          {
            'featureType': 'poi.park',
            'elementType': 'labels.text.stroke',
            'stylers': [
              {
                'color': '#1b1b1b'
              }
            ]
          },
          {
            'featureType': 'road',
            'elementType': 'geometry.fill',
            'stylers': [
              {
                'color': '#2c2c2c'
              }
            ]
          },
          {
            'featureType': 'road',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#8a8a8a'
              }
            ]
          },
          {
            'featureType': 'road.arterial',
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#373737'
              }
            ]
          },
          {
            'featureType': 'road.highway',
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#3c3c3c'
              }
            ]
          },
          {
            'featureType': 'road.highway.controlled_access',
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#4e4e4e'
              }
            ]
          },
          {
            'featureType': 'road.local',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#616161'
              }
            ]
          },
          {
            'featureType': 'transit',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#757575'
              }
            ]
          },
          {
            'featureType': 'water',
            'elementType': 'geometry',
            'stylers': [
              {
                'color': '#000000'
              }
            ]
          },
          {
            'featureType': 'water',
            'elementType': 'labels.text.fill',
            'stylers': [
              {
                'color': '#3d3d3d'
              }
            ]
          }
        ]
      }

    }
  },
  created () {
    this.currentMarker = this.markers[this.currentTab.nameCity]
  },
  watch: {
    currentTab: {
      handler () {
        this.currentMarker = this.markers[this.currentTab.nameCity]
      }
    }
  }
}
</script>
