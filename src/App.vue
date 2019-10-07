<template>
  <div id="app">
    <Contacts/>
  </div>
</template>

<script>
import Contacts from './components/contacts/contacts.vue'

export default {
  name: 'app',
  components: {
    Contacts
  }
}
</script>
<style>
  #app {
    display: flex;
    justify-content: center;
    align-items: center
  }
</style>
<style lang="scss" src="./scss/style.scss"></style>
