<template>
<div class="">
  <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
    <div class="mb-4">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="name">
        Name
      </label>
      <input v-model="name" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="name" type="text" placeholder="Name" />
    </div>
    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="email">
        Email
      </label>
      <input v-model="email" class="shadow appearance-none border  rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="email" type="email" placeholder="email"  />
      <p class="text-red-500 text-xs italic">Your best email.</p>
    </div> 
    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="phone">
        Phone
      </label>
      <input v-model="phone" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="phone" type="tel" placeholder="phone" />
      <p class=" text-xs italic">Your phone number with area code.</p>
    </div> 

    <div class="mb-6">
      <label class="block text-gray-700 text-sm font-bold mb-2" for="avatar">
        Avatar
      </label>
      <input v-model="avatarImg" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline" id="avatar" type="text" placeholder="avatar" />
      <p class=" text-xs italic">Upload your avatar img.</p>
    </div> 

    <div class="flex items-center justify-between">
      <a class="inline-block align-baseline font-bold text-sm text-red-500 hover:text-red-800" href="#">
        Clear All
      </a>
      <button @click="submitUser" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="button">
        Submit
      </button>
    </div>
  </form>
</div>

</template>

<script>
export default {
  data ()  {
    return {
      name: '',
      email: '',
      phone: null,
      avatarImg: ''
    }
  },
  methods: {
    submitUser () {
      this.$emit('submitUser', {
        name: this.name,
        email: this.email,
        phone: this.phone,
        avatarImg: this.avatarImg
      })
    }
  }
};
</script>
