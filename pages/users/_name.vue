<template>
  <div>
    <h1>Hello, {{name}}!</h1>
  </div>
</template>
<script>
export default {
  asyncData({params}) {
    return {
      name: params.name
    }
  }
}
</script>