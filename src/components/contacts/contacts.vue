<template>
  <section class="contacts">
    <div class="container">
      <div class="contacts__header">
        <h2 class="contacts__title title-h2">Contacts</h2>
      </div>
      <OfficeAndSupport/>
    </div>
  </section>
</template>

<script>
import OfficeAndSupport from './componets/OfficeAndSupport'

export default {
  name: 'Contacts',
  components: {
    OfficeAndSupport
  }
}
</script>
