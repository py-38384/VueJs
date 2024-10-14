<script setup>
      import { ref, onMounted } from 'vue'; 
      const user = ref('Piyal Hossein')
      const status = ref('active')
      const friends = ref(['mursalin', 'minarul', 'ridoy', 'rakib'])
      const newTask = ref('mottakin')

      const addFriend = () => {
        if (newTask.value){
          friends.value.push(newTask.value)
          newTask.value = ''
        }
      }

      const deleteFriend = (index) => {
        friends.value.splice(index, 1)
      }

      const link = ref('https://www.google.com')
      const toggle_status = () => {
        if(status.value === 'active'){
          status.value = 'pending'
        }else if(status.value === 'pending'){
          status.value = 'inactive'
        }else{
          status.value = 'active'
        }
      }
      onMounted(async () => {
        try {
          const response = await fetch('	https://jsonplaceholder.org/users')
          const data = await response.json()
          console.log(data)
          friends.value = data.map(user => `${user.firstname} ${user.lastname}`)
        } catch (error) {
          console.log('Error fetching tasks')
        }
      })
</script>

<template>
  <h1>{{user}}</h1>
  <div v-if="status === 'active'">{{ user }} is active</div>
  <div v-else-if="status === 'pending'">{{ user }} is pending</div>
  <div v-else>{{ user }} is inactive</div>

  <form @submit.prevent="addFriend">
    <label for="newFriend">Add Friend</label><br>
    <input type="text" id="newFriend" name="newFriend" v-model="newTask"><br>
    <button type="submit">Submit</button>
  </form>

  <div v-if="friends">
    <div>{{ user }} has some friend</div>
    <ul>
      <li v-for="(friend, index) in friends" v-bind:key="friend">
        <span>{{ friend }}</span>
        <button @click="deleteFriend(index)">x</button>
      </li>
    </ul>
  </div>
  <a v-bind:href="link">Google</a>
  <a :href="link">Google</a>
  <br>
  <button @click="toggle_status">Change Status</button>
</template>

<style>
  h1{
    color: red;
  }
</style>