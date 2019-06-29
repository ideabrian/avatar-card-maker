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
      <p class="text-xs italic">Your best email.</p>
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
      <p class=" text-xs italic">Link to your avatar img.</p>
    </div> 

    <div class="flex items-center justify-between">
      <button @click.prevent="clearUser" class="bg-green-300 hover:bg-green-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
        Clear All
      </button>
      <div class="">{{ clear ? " empty " : " filled " }}</div>
      <button @click="submitUser" :class="[submitButtonActiveClasses]" type="button" :disabled="true">
        Submit
      </button>
    </div>
  </form>
</div>

</template>

<script>
function initialState() {
    return {
      name: 'Jack Lyons',
      email: 'jack@example.com',
      phone: '(212) 555-1234',
      avatarImg: 'https://www.w3schools.com/howto/img_avatar.png',
      clear: false,
      submitButtonActiveClasses: ['bg-blue-500', 'hover:bg-blue-700', 'text-white', 
                                 'font-bold', 'py-2', 'px-4', 'rounded', 'focus:outline-none', 'focus:shadow-outline']
    }
}

function clearState() {
    return {
      name: '',
      email: '',
      phone: '',
      avatarImg: '',
      clear: true,
      submitButtonActiveClasses: ['bg-blue-300',  'text-white', 
                                 'font-bold', 'py-2', 'px-4', 'rounded', 'focus:outline-none', 'focus:shadow-outline']
    }
}
export default {
  data ()  {
    return initialState();
  },
  
  methods: {
    submitUser () {
      this.$emit('submitUser', {
        name: this.name,
        email: this.email,
        phone: this.phone,
        avatarImg: this.avatarImg
      })
      this.clearUser()
    },
    clearUser() {
      Object.assign(this.$data, clearState());
    }
  }
};
</script>
