# Sample Nuxt.js site

## Nuxt cheat sheet

### How to add a page

Go to `pages` and create a new vue component file. Your new page will be located based on the name of the file. i.e. if you want an about-me page, create an about-me.vue file.

For example, if I want a page to have a URL of `my-site.com/about/me`, I would create the following structure within the `pages` folder:

```
.
└── pages/
    ├── about/
        └── me.vue
```

This automatically creates the correct routing for you.

### Components
The `components` folder should hold smaller components to be re-used in your pages files.

To import a component:
1. in `script` tag, import the component using its absolute path `~/components/ComponentName.vue`

1. in `export default` add

```js
export default {
  components: {
    ComponentName
  }
}
```

You can then use the component in your `template` as such:

```html
<template>
  <div>
    <ComponentName />
  </div>
</template>
```

### Data basics

#### Static data
If you need to work with **static** data, use the `data` attribute.

```js
export default {
  data () {
    return {
      name: 'My name',
    }
  }
}
```

`name` is then available as a property you can use in your template using template literals `<p>{{ name }}</p>`

#### Data that needs computation

If you need data that requires any sort of computing (i.e. working with a date, working with any math, or maybe string manipulation), you'll want to use the `computed` property.

In `<script>` tag:

```js
export default {
  computed: {
    today () {
      return new Date()
    }
  }
}
```

This data is then available in your template just like any other data property: 

```html
<template>
  <div>
    <p>Today's date: {{ today }}</p>
  </div>
</template>

```

#### Data from an API

If you need to retrieve data from an API, you can use the async property.

```js
export default {
  asyncData({ $axios }) {
    let { data } = await $axios.get("/user/1");
    return { user: data };
  }
}
```

When working with asyncData, remember the data may not be avaiable right when you load the page / component, so make sure you have some fallbacks.

For example, if I were making a call to the fake endpoint above to get user data, I would then use this data in the template like so:

```html
<template>
  <div>
    <div v-if="user">
       <!-- user data goes here -->
    </div>
    <div v-else>
      <p>...loading</p>
    </div>
  </div>
</template>
```

**A note on console.logging async data:** If you wanted to console log async data, you need to do this in what's known as the `mounted` hook. This is because async data is not available until the component is mounted.

If I wanted to `console.log` the data above (i.e. the `user` data I got from my fake API), I would do this in the mounted hook as such:

```js
export default {
  asyncData({ $axios }) {
    let { data } = await $axios.get("/user/1");
    return { user: data };
  },

  mounted () {
    console.log(this.user);
  }
}
```

## More resources to learn

* [Your first Vue app](https://flaviocopes.com/vue-first-app/): Good starting point
* [Vue Mastery](https://www.vuemastery.com/): Great videos, some are free!
* [Contentful Blog in 5 minutes](https://github.com/contentful/blog-in-5-minutes): Absolute must to get a blog up and running for free!
* [Getting started with Vue](https://www.taniarascia.com/getting-started-with-vue/): Really thorough tutorial!
* [Awesome Vue](https://github.com/vuejs/awesome-vue): Other cool resources


## Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).
