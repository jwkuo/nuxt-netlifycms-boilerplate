<template lang="html">
  <div class="post">
    <div class="featured-image">
      <img v-if="thumbnail" :src="thumbnail" alt="Thumbnail">
    </div>
    <h1 class="title">{{title}}</h1>
    <p class="date">Posted by {{author}} on {{date}}</p>
    <div class="body" v-html="$md.render(body)"/>
    <p class="back"><a class="back-link" @click="$router.back()">Back</a></p>
  </div>
</template>

<script>
export default {
  async asyncData({ params, app, payload, route, store }) {
    /*
    Interestingly, if you just return the raw post object as it is imported,
    Nuxt fails to build, but if you create your own object with the data you
    need, it works. The issue is discussed here, but apparently it wasn't
    completely fixed. https://github.com/nuxt-community/apollo-module/issues/163
    However, I like the code more this way anyway--it's more explicit what
    you're bringing in from the JSON.
    */
    let post = await import(`~/content/blog/${params.slug}.json`);
    return {
      date: post.date,
      body: post.body,
      title: post.title,
      author: post.author,
      thumbnail: (typeof post.thumbnail !== 'undefined') ? post.thumbnail : null
    };
  }
}
</script>

<style lang="css" scoped>
.back, .date, .body {
  padding-top: 10px;
}
.back-link {
  text-decoration: underline;
  color: #3b8070;
  cursor: pointer;
}

.date {
  color: darkgray;
}
.post {
  background-color: whitesmoke;
  padding: 20px;
}
.featured-image {
  margin: 10px auto;
  text-align: center;
}
.featured-image img {
  max-width: 300px;
}
</style>
