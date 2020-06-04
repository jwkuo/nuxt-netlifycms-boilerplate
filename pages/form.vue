<template lang="html">
  <div class="post">
    <h1 class="title">Test Form</h1>
    <form name="test-form" method="post" data-netlify="true" data-netlify_honeypot="bot-field">
      <input type="hidden" name="form-name" value="test-form" />
      <label>
        <span>First Name</span>
        <input type="text" name="first-name" />
      </label>
      <button>Submit</button>
    </form>
    <p class="back"><a class="back-link" @click="$router.back()">Back</a></p>
  </div>
</template>

<script>
export default {
  name: "TestForm",
  data () {
    return {}
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
