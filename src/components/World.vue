<template>
    <div>
        <p>
            <select v-model="name">
                <option :key="op.key" v-for="op in ops">{{op.name}}</option>
            </select>
        </p>
        <p>{{name}}</p>
    </div>
</template>

<script>
export default {
  name: 'World',
  data(){
    return {
        name:null,
      ops:[{key:1,name:'leonel'},{key:2,name:'lopez'}]
    }
  }
}
</script>

<style scoped>

</style>
