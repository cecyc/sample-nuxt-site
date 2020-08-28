<template>
  <div class="container">
    <header>
      <h1>Catlyn Meowington</h1>
    </header>
    <section class="bio">
      <p>{{ bio }}</p>
      <p>My favorite foods are</p>
    <ul v-for="(food, idx) in favoriteFood" :key="idx">
      <li>{{ food }}</li>
    </ul>
    </section>
  </div>
</template>

<script>

export default {
  data () {
    return {
      bio: "Hello! I'm Catlyn, a meowser experience designer.",
      favoriteFood: ['fish', 'sushi', 'pizza']
    }
  },
}
</script>

<style>
.container {
  width: 80%;
  margin: 0 auto;
}

header {
  display: flex;
  justify-content: center;
  align-content: center;
  align-items: center;
  padding: 2rem 0;
  border-bottom: 2px solid turquoise;
}

.profile {
  border-radius: 100%;
  width: 100px;
  height: 100px;
  margin-right: 2rem;
}

.bio {
  padding: 2rem;
}
</style>
