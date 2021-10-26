<template>
  <div>
    <h1>{{title}}</h1>
    <img :src="image" :alt="title">
  </div>
</template>
<script>
export default {
  data() {
    return {
      title: '',
      image: ''
    }
  },
  async mounted() {
    const response = await fetch(`https://api.spoonacular.com/recipes/${this.$route.params.id}/information?apiKey=c5d833c8ea6e4742953e7a6380196931`);

    if(!response.ok) {
      console.error(`Error ${response.error}`);
      return;
    }
    const recipe = await response.json();
    this.title = recipe.title;
    this.image = recipe.image;
  }
}
</script>
