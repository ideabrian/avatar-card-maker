<template>
  <div id="app">

    <section class="bg-gray-400 h-screen">
      <!-- Two columns -->
      <div class="flex flex-col-reverse md:flex-row items-center justify-center">
        <div class="w-full md:w-1/2 p-4">
          <InputCard @submitUser="logItOut" />
        </div>
        <div class="w-full md:w-1/2 p-4">
          <OutputCard
            :name="name"
            :email="email"
            :phone="phone"
            :avatarImg="avatarImg"
          />
        </div>
      </div>
    </section>

  </div>
</template>

<script>
import InputCard from './components/InputCard'
import OutputCard from './components/OutputCard'

export default {
  name: 'app',
  components: {
    OutputCard,
    InputCard
  },
  data() {
    return {
      name: '',
      email: '',
      phone: '',
      avatarImg: ''
    }
  },
  methods: {
    logItOut ({ name, email, phone, avatarImg }) {
      // eslint-disable-next-line
      this.name = name
      this.email = email
      this.phone = phone
      this.avatarImg = avatarImg
    }
  }
}
</script>
