<template>
  <div class="alert" :class="additionalClass" role="alert">
    <strong>{{title}}</strong> {{text}}
  </div>
</template>

<script>
  export default {
    props: ['type', 'title', 'text'],
    computed: {
      additionalClass () {
        if (!this.type) {
          return 'alert-success'
        }

        return 'alert-' + this.type
      }
    },
    name: 'alert'
  }
</script>
