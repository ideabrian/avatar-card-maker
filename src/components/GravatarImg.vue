<template>
  <img :src="url" :alt="alt" class="block h-16 sm:h-24 rounded-full mx-auto mb-4 sm:mb-0 sm:mr-4 sm:ml-0"/>
</template>

<script>
  import md5 from 'md5';

  export default {
    name: 'GravatarImg',

    props: {
      email: {
        type: String
      },

      hash: {
        type: String,
        default: ''
      },

      size: {
        type: Number,
        default: 180
      },

      defaultImg: {
        type: String,
        default: 'retro'
      },

      rating: {
        type: String,
        default: 'g'
      },

      alt: {
        type: String,
        default: 'Avatar'
      }
    },

    computed: {
      url() {
        const img = [
          '//www.gravatar.com/avatar/',
          this.hash || md5(this.email.trim().toLowerCase()),
          `?s=${this.size}`,
          `&d=${this.defaultImg}`,
          `&r=${this.rating}`
        ];

        return img.join('');
      }
    }
  };
</script>
