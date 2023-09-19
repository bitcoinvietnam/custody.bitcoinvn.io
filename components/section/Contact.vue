<template>
  <section id="contact" class="text-white bg-dark-blue/30 section">
    <div class="w-full overflow-y-auto md:w-3/6 section-ctn">
      <div class="text-gold-500 header">
        Contact Us
      </div>
      <div class="paragraph">
        <form class="flex flex-col space-y-3">
          <input type="text" v-model="email" id="email" placeholder="Enter Your Email Address"
            class="w-full p-2 text-base font-bold text-center text-white rounded-lg placeholder:text-gray-300 placeholder:font-normal placeholder:text-sm bg-gray-100/50 md:p-3 md:text-lg" />
          <div v-if="!isValidEmail" class="pt-1 text-red-500">
            Please enter a valid email address.
          </div>
          <input type="tel" id="phone" v-model="phone" placeholder="Your Telephone Number"
            class="w-full p-2 text-base font-bold text-center text-white rounded-lg placeholder:text-gray-300 placeholder:font-normal placeholder:text-sm bg-gray-100/50 md:p-3 md:text-lg" />
          <div v-if="!isValidPhone" class="text-red-500">
            Please enter a valid phone number.
          </div>
          <input type="text" v-model="telegram" id="telegram" placeholder="Your Telegram Handle"
            class="w-full p-2 text-base font-bold text-center text-white rounded-lg placeholder:text-gray-300 placeholder:font-normal placeholder:text-sm bg-gray-100/50 md:p-3 md:text-lg" />
          <div v-if="!isValidTelegram" class="text-red-500">
            Please enter a valid Telegram handle.
          </div>
          <textarea id="message" v-model="message" rows="6" placeholder="Your Message"
            class="w-full p-2 text-sm text-gray-200 rounded-lg placeholder:text-gray-300 placeholder:font-normal placeholder:text-sm bg-gray-300/50 md:p-3 md:text-sm" />
        </form>
        <div v-if="successResp" class="text-green-600">
          <div class="text-sm">
            Thank you for contacting us. We will get back to you shortly via the provided email.
          </div>
          <div class="text-sm text-gray-500">
            We reply within the same day - please also check your spam folder carefully.
            You can safely close this tab now.
          </div>
        </div>
      </div>
      <div class="pt-3">
        <BtnMain :onclick="submit">Submit</BtnMain>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: '',
      message: '',
      phone: '',
      telegram: '',
      endpoint: 'https://formspree.io/f/mvojqwjj',
      isValidEmail: true,
      isValidPhone: true,
      isValidTelegram: true,
      successResp: false
    }
  },
  methods: {
    validateEmail(email) {
      if (!email) {
        return false
      }
      if (/^\w+([.-]?\w+)*@\w+([.-]?\w+)*(\.\w{2,3})+$/.test(email)) {
        return true
      }
      return false
    },

    validatePhone(phone) {
      if (!phone) {
        return false
      }
      return true
    },

    validateTelegram(handle) {
      if (!handle) {
        return false
      }
      return true
    },

    async submit() {
      this.successResp = false
      this.isValidEmail = this.validateEmail(this.email)
      this.isValidPhone = this.validatePhone(this.phone)
      this.isValidTelegram = this.validateTelegram(this.telegram)
      if (!this.isValidEmail || !this.isValidPhone || !this.isValidTelegram) {
        return false
      }
      const data = {
        email: this.email,
        message: this.message,
        phone: this.phone,
        telegram: this.telegram,
      }
      // Formspree side will send an email for confirmation.
      // So we just display a thank you note here
      this.successResp = true
      const resp = await fetch(this.endpoint, {
        method: 'POST',
        body: JSON.stringify(data)
      })
    },
  },
}
</script>