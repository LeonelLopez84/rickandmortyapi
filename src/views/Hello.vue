<template>
  <div class="hello">
    <div class="container mx-auto">
    <h1 class="text-3xl font-bold underline">
    Hello world!
  </h1>
    <table class="table w-full">
      <thead>
        <tr>
          <th>id</th>
          <th>name</th>
          <th>species</th>
          <th>type</th>
          <th>gender</th>
          <th>image</th>
        </tr>
      </thead>
      <tbody>
          <tr :key="chara.id" v-for="chara in characters">
              <td>{{chara.id}}</td>
              <td>{{chara.name}}</td>
              <td>{{chara.species}}</td>
              <td>{{chara.type}}</td>
              <td>{{chara.gender}}</td>
              <td>
                <vue-load-image>
                  <template v-slot:image>
                    <img :src="chara.image"/>
                  </template>
                  <template v-slot:preloader> 
                    <img src="../assets/128x128.gif" />
                  </template>
                  <template v-slot:error>Image load fails</template>
                </vue-load-image>
                </td>
          </tr>
      </tbody>
    </table>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import VueLoadImage from 'vue-load-image'

export default {
  name: 'Hello',
  components:{
    'vue-load-image': VueLoadImage
  },
  data(){
    return {
      characters:[]
    }
  },
  beforeCreate(){
    axios.get('https://rickandmortyapi.com/api/character')
      .then((result) => {
         this.characters = result.data.results
         console.log(result)
      }).catch(function (error) {
          console.log(error)
      });
  }
}
</script>
