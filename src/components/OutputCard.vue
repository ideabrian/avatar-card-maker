<template>
  <div class="mx-auto py-10">
    <div class="border m-6 rounded-lg bg-white mx-auto max-w-sm shadow-lg rounded-lg overflow-hidden">
      <div class="sm:flex sm:items-center px-6 py-4">
        <div v-if="avatarImg">
          <img
          class="block h-16 sm:h-24 rounded-full mx-auto mb-4 sm:mb-0 sm:mr-4 sm:ml-0"
          :src="avatarImg"
          alt="Avatar image"
        >
        </div>
        <div v-else="">
          <!-- Show default image so people know what it looks like-->
          <span class="mt-16 ml-8 z-50 absolute text-white">hi!</span>
          <img 
          class="block h-16 sm:h-24 rounded-full mx-auto mb-4 sm:mb-0 sm:mr-4 sm:ml-0"
          src="/jack_avatar.jpeg" 
          alt="Jack" />
        </div>
        <div class="text-center sm:text-left sm:flex-grow">
          <div class="mb-4">
            <p class="text-xl leading-tight">{{ name }}</p>
            <p class="text-m leading-tight">{{ email }}</p>
            <p class="text-sm leading-tight text-grey-dark">{{ phone }}</p>
          </div>
          <div class="flex flex-wrap">
            <button
              class="text-xs font-semibold rounded-full px-4 py-1 mx-3 leading-normal bg-white border border-blue text-blue hover:bg-blue hover:text-white"
            >Email</button>
            <button
              class="text-xs font-semibold rounded-full px-4 py-1 leading-normal bg-white border border-purple text-purple hover:bg-purple hover:text-white"
            >Call</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "OutputCard",
  props: {
    name: {
      type: String,
      default: ''
    },
    email: {
      type: String,
      default: ''
    },
    phone: {
      type: [String, Number],
      default: ''
    },
    avatarImg: {
      type: String,
      default: ''
    }
  }
};
</script>
