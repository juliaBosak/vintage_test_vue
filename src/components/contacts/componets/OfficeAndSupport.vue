<template>
  <section class="contacts__section">
    <div class="container">
      <div class="contacts__header">
        <h2 class="contacts__title title-h2">Contacts</h2>
      </div>
      <div class="office-and-support contacts__row">
        <article class="contacts__office">
          <header class="contacts__office-header">
            <h3 class="title-h3"><span class="green-text">GMS</span> Headquarters</h3>
          </header>
          <div class="contacts__office-content">
            <div class="contacts__office-description">
              <div class="contacts__office-address">
                <p class="paragraph">
                  Global Message Services Ukraine LLC <br>
                  Bundesstrasse 5 | 3rd Floor <br>
                  6300 Zug <br>
                  Switzerland
                </p>
              </div>
              <div class="contacts__office-phone">
                <a class="phone" href="tel:+41415446200">+41 41 544 62 00</a>
              </div>
            </div>
            <div class="contacts__office-links">
              <div class="contacts__link-wrap">
                <div class="contacts__link-title">
                  <h6 class="paragraph">
                    Email
                  </h6>
                </div>
                <div class="contacts__link">
                  <a class="link" href="mailto:info@gms-worldwide.com">info@gms-worldwide.com</a>
                </div>
              </div>
              <div class="contacts__link-wrap">
                <div class="contacts__link-title">
                  <h6 class="paragraph">
                    Send message
                  </h6>
                </div>
                <div class="contacts__link">
                  <a class="link"  v-if="isMobile()" href="viber://add?number=41415446200">Viber us</a>
                  <a class="link"  v-else href="viber://chat?number=41415446200">Viber us</a>
                </div>
              </div>
              <div class="contacts__link-wrap">
                <div class="contacts__link-title">
                  <h6 class="paragraph">
                    Send form
                  </h6>
                </div>
                <div class="contacts__link">
                  <a class="link" href="#contacts__form">Contact us</a>
                </div>
              </div>
            </div>
          </div>
        </article>
        <article class="contacts__support">
          <header class="contacts__support-header">
            <h3 class="title-h3"> Technical support<span class="green-text"> 24/7</span> </h3>
          </header>
          <div class="contacts__support-description">
            <p class="paragraph">
              GMS understands that it can be hard to follow all new technologies. We regularly provide for all our clients educational trainings to make your operator`s business earn more and better though our best practices.
            </p>
          </div>
          <div class="contacts__support-phone">
            <a class="phone" href="tel:+41415446206">+41 41 544 62 06</a>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'OfficeAndSupport',
  methods: {
    isMobile () {
      if (/Android|webOS|iPhone||iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)) {
        return true
      } else {
        return false
      }
    }
  }
}
</script>
