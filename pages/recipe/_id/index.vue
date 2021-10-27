<template>
  <div>
    <h1>{{title}}</h1>
    <img :src="image" :alt="title">
  </div>
</template>
<script>
import axios from 'axios';
export default {
  asyncData({route, params}) {
    return new Promise((resolve, reject) => {
      axios.get(`https://api.spoonacular.com/recipes/${params.id}/information?apiKey=c5d833c8ea6e4742953e7a6380196931`)
      .then(({data}) => {
        resolve(data);
      }).catch(err => {
        reject(err);
      });
    });
  }
}
</script>
