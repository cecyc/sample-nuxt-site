<template>
  <div class="container">
    <header>
      <img :src="catImg" alt="a cat" class="profile">
      <h1>Catlyn Meowington</h1>
    </header>
    <section class="bio">
      <p>{{ bio }}</p>
    </section>
    <section class="blog-container">
      <div class="post" v-for="(post, idx) in fakeBlog" :key="idx">
        <h2>{{ post.title }}</h2>
        <p class="date">{{ post.date }}</p>
        <p>{{ post.blurb }}</p>
        <p>{{ post.body }}</p>
      </div>
    </section>
  </div>
</template>

<script>
import cat from '~/assets/images/catto.png'
import fakeBlog from '~/static/fakeBlog.js'

export default {
  data () {
    return {
      catImg: cat,
      bio: "Hello! I'm Catlyn, a meowser experience designer.",
      fakeBlog: fakeBlog,
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

.blog-container {
  padding: 2rem;
  display: flex;
}

.blog-container p {
  margin-bottom: 1rem;
}

.date {
  font-style: italic;
}

.post {
  width: 30%;
  margin-right: 2rem;
}
</style>
