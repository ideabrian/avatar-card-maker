<template>
<div class="">
  <form class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
    <div class="mb-4">
      <div class="mb-4">
        <input class="" type="checkbox" id="developer" name="developer"  v-model="developer">
        <span class="ml-2 text-xs mb-4">Developer Mode</span>
      </div>
      <label class="block text-gray-700 text-sm font-bold mb-2" for="name">
        Name
      </label>
      <input v-model="name" class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="name" type="text" placeholder="Name" required/>
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
      <button v-if="name.length>0" @click.prevent="clearUser" class="bg-green-500 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">
        {{ name.length===0 ? "disabled" : "clear all" }}
      </button>
      <button v-else @click.prevent="clearUser" class="bg-gray-500 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline  cursor-not-allowed">
        {{ name.length===0 ? "disabled" : "clear all" }}
      </button>
      
      <button v-if="name.length>0" @click="submitUser" :class="[submitButtonActiveClasses]" type="button">
        {{ name.length===0 ? "disabled" : "Submit"}}
      </button>
      <button v-else @click="submitUser" class="bg-gray-500 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline cursor-not-allowed" type="button" :disabled="name.length===0">
        {{ name.length===0 ? "disabled" : "Submit"}}
      </button>
    </div>
    <!-- Put the output of the behind the scenes stuff here -->
    
    <div v-if="developer" style="backgroundColor: black; color: lime" class="text-white mt-6 py-2 px-4">
    <h1 class="text-xl text-red-600">Developer Mode</h1>
    <pre>
        <ul>
          <li>{{ name.length===0 ? " name: empty " : " name: not empty " }}</li>
          <li>{{ email.length===0 ? " email: empty " : " email: not empty " }}</li>
          <li>{{ phone.length===0 ? " phone: empty " : " phone: not empty " }}</li>
          <li>{{ avatarImg.length===0 ? " avatarImg: empty " : " avatarImg: not empty " }}</li>
          </ul>
      <span class="text-red-600">Example values:</span>
      <div>name.length: {{ name.length }}</div>
      <div>submitButtonStatus: {{ submitButtonStatus }}</div>
      Initial State Values
      <div>name field length as boolean: {{ name.length === 0 }}</div>
      </pre>
  </div>
  </form>
</div>
</template>

<script>
function initialState() {
  console.log("initialState'd")
  let name = 'Jack Lyons';
    return {
      name,
      email: 'jack@example.com',
      phone: '(212) 555-1234',
      avatarImg: 'https://www.w3schools.com/howto/img_avatar.png',
      clear: false,
      submitButtonActiveClasses: ['bg-blue-500', 'hover:bg-blue-700', 'text-white', 
                                 'font-bold', 'py-2', 'px-4', 'rounded', 'focus:outline-none', 'focus:shadow-outline'],
      submitButtonStatus: {active:true},
      developer: true // true turns on the data preview that's partially implemented
    }
}

function clearState() {
  console.log("clearState'd")
    return {
      name: '',
      email: '',
      phone: '',
      avatarImg: '',
      clear: true
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
      // this.clearUser()
    },
    clearUser() {
      Object.assign(this.$data, clearState());
    }
  }
};
</script>
