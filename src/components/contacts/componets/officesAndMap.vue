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
  name: 'contactsMap',
  props: {
    currentTabs: Array,
    currentMarkers: Object,
    currentStyle: Array
  },
  data () {
    return {
      tabs: this.currentTabs,
      currentTab: this.currentTabs[0],
      markers: this.currentMarkers,
      currentMarker: null,
      mapStyle: {
        zoomControl: false,
        mapTypeControl: false,
        streetViewControl: false,
        fullscreenControl: false,
        styles: this.currentStyle
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
