<style>
  h1{
    color: red;
  }
</style>

<template>
  <h1>{{user}}</h1>
  <div v-if="status === 'active'">{{ user }} is active</div>
  <div v-else-if="status === 'pending'">{{ user }} is pending</div>
  <div v-else>{{ user }} is inactive</div>
  <div v-if="friends">
    <div>{{ user }} has some friend</div>
    <ul>
      <li v-for="friend in friends" v-bind:key="friend">{{ friend }}</li>
    </ul>
  </div>
  <a v-bind:href="link">Google</a>
  <a :href="link">Google</a>
  <br>
  <button @click="toggle_status">Change Status</button>
</template>

<script>
  export default {
    data (){
      return {
        user: 'Piyal Hossein',
        status: 'active',
        friends: ['mursalin', 'minarul', 'ridoy', 'rakib'],
        link: 'https://www.google.com'
      }
    },
    methods: {
      toggle_status(e){
        if(this.status === 'active'){
          this.status = 'pending'
        }else if(this.status === 'pending'){
          this.status = 'inactive'
        }else{
          this.status = 'active'
        }
      }
    }
  }
</script>