<template>
  <div class="contacts">
      <OfficeAndSupport/>
    <OfficesAndMap v-bind:currentTabs="tabs" v-bind:currentMarkers="markers" v-bind:currentStyle="style"/>
    <ContactsForm/>
  </div>
</template>

<script>
import OfficeAndSupport from './componets/OfficeAndSupport'
import OfficesAndMap from './componets/officesAndMap'
import ContactsForm from './componets/contactsForm'
export default {
  name: 'Contacts',
  components: {
    OfficeAndSupport,
    OfficesAndMap,
    ContactsForm
  },
  data () {
    return {
      tabs: [
        {
          nameCity: 'Kyiv',
          place: 'Global Message Services Ukraine LLC',
          address: 'Kyiv, Stepan Bandera, 33 \n 02066 \n Ukraine'
        },
        {
          nameCity: 'New York',
          place: 'Stevens Institute of Technology',
          address: 'New York, Hoboken \n NJ 07030\n  The USA'
        },
        {
          nameCity: 'Guangzhou',
          place: 'Guangzhou Rural Commercial',
          address: 'Guangzhou \n Huangpu \n China'
        },
        {
          nameCity: 'Barcelona',
          place: 'Palau de la Generalitat de Catalunya',
          address: 'Barcelona, Plaça de Sant Jaume, 4 \n 08002 \n Spain'
        }
      ],
      markers: {
        'Kyiv': { lat: 50.4891897, lng: 30.4873203 },
        'New York': { lat: 40.7341777, lng: -74.131975 },
        'Guangzhou': { lat: 23.3278454, lng: 113.1255902 },
        'Barcelona': { lat: 41.383962, lng: 2.1740104 }
      },
      style: require('../../assets/map/googleMapStyle.json')
    }
  }

}
</script>
