<template>
  <section class="contacts__section contacts__form-section">
    <div class="container">
      <header >
        <h3 class= "form__header title-h3">Contacts Us</h3>
      </header>
      <div class="contacts__row">
            <form id="contactsForm"
                  action="http://httpbin.org/post"
                  method="post"
                  class="contacts__form form">
              <div class="form__field-wrap">
                  <input
                    class="form__field"
                    type="text"
                    v-model="name"
                    v-bind:class="{ error: isNameError }"
                    @blur="isNameTouched = true"
                  >
                <label class="form__label">Name</label>
                <div class="form__error-message" v-if="isNameError">
                  Enter your name
                </div>
              </div>
              <div class="form__field-wrap">
                  <input
                    class="form__field"
                    type="text"
                    v-model="phone"
                    v-bind:class="{ error: isPhoneError }"
                    @blur="isPhoneTouched = true"
                   >
                <label class="form__label">Phone</label>
                <div class="form__error-message" v-if="isPhoneError">
                  Enter your phone
                </div>
              </div>
              <div class="form__field-wrap">
                  <input
                    class="form__field"
                    type="text"
                    v-model="email"
                    v-bind:class="{ error: isEmailError }"
                    @blur="isEmailTouched = true">
                <label class="form__label">E-mail</label>
                <div class="form__error-message" v-if="isEmailError">
                  Enter your email
                </div>

              </div>
              <div class="form__checkbox-wrap">
                  <input
                    type="checkbox"
                    class="form__checkbox"
                    v-model="isAgree"
                    @blur="isCheckboxTouched = true"
                    v-bind:class="{ error: !isAgree && isCheckboxTouched }"
                  >
                <label class="form__checkbox-label">I agree the processing of personal data</label>
                <div class="form__error-message" v-if="!isAgree && isCheckboxTouched">
                  Please, agree the processing of personal data
                </div>
              </div>
              <div class="form__button-wrap">
                <button
                  class="form__button"
                  :disabled="false"
                type="submit">Get in touch</button>
              </div>
            </form>
            <div class="contacts__form-description">
              <p class="contacts__form-text">
                Please tell us more about your request and give us info about your company and country
              </p>
            </div>
          </div>
    </div>
  </section>

</template>
<script>
const emailCheckRegex = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
const phoneCheckRegex = /[0][1-9]{9}/;
export default {
  name: 'Form',
  data () {
    return {
      name: null,
      phone: null,
      email: null,
      isAgree: false,
      isEmailTouched: false,
      isNameTouched: false,
      isPhoneTouched: false,
      isCheckboxTouched: false
    }
  },
  computed: {
    isEmailValid () {
      return emailCheckRegex.test(this.email)
    },
    isEmailError () {
      return !this.isEmailValid && this.isEmailTouched
    },
    isPhoneValid () {
      return phoneCheckRegex.test(this.phone)
    },
    isPhoneError () {
      return !this.isPhoneValid && this.isPhoneTouched
    },
    isNameError () {
      return !this.name && this.isNameTouched
    }
  }

}
</script>
