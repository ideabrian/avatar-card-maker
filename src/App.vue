<template>
  <div id="app">

    <section class=" bg-gray-400">
      <!-- Two columns -->
      <div class="flex flex-col-reverse md:flex-row items-center  h-screen justify-center">
        <div class="w-full md:w-1/2 p-4">
          <InputCard @submitUser="logItOut" />
        </div>
        <div class="w-full md:w-1/2 p-4">
          <ProfileCard
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
import ProfileCard from './components/ProfileCard'

export default {
  name: 'app',
  components: {
    ProfileCard,
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

