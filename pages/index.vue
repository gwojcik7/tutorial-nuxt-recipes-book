<template>
  <div>
    <ul>
      <li v-for="(recipe, index) in recipes" :key="index">
        <img :src="recipe.image" :alt="recipe.sourceName">
        <h3>
          <nuxt-link :to="`/recipe/${recipe.id}`">
            {{recipe.title}}
          </nuxt-link>
        </h3>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      recipes: []
    }
  },
  async mounted() {
    const response = await fetch('https://api.spoonacular.com/recipes/random?apiKey=c5d833c8ea6e4742953e7a6380196931', {response: 'json'});

    if(!response.ok) {
      console.error(`Error ${response.error}`);
      return;
    }
    const recipes = await response.json();
    this.recipes = recipes["recipes"];
    console.log(this.recipes);
  }
}
</script>
