<template>
  <header>
    <h1>{{ name }}</h1>
  </header>
</template>
<script>
export default {
  props: {
    name: {
      type: String,
      required: true,
      default: 'Your name here'
    }
  }
}
</script>