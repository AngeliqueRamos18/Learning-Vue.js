
<script setup>
// With composition API wrap everything with setup function (can also be done by adding setup keyword beside script for shorter)

// unlike the option api, there is no need for data() function

//In order for the buttons to be able to change the status we need to make it reactive with ref
import { onMounted, ref } from 'vue';

// This time we will create the composition API, a later version than Options API
    
    // Make them reactive variable with ref, and when you are calling the value instead of this.status it will be status.value
    const name = ref('Angel');
    const status = ref(true);
    const status_txt = ref('active');
    const tasks = ref(['Task One', 'Task Two', 'Task Three']);
    const newTask = ref('');

    const toggleStatus = () => {
      if(status_txt.value === 'active'){
        status_txt.value = 'pending';
      }
      else if(status_txt.value === 'pending'){
        status_txt.value = 'inactive';
      }
      else{
        status_txt.value = 'active';
      }
    };

    // What this does is to add the value input to the tasks list, and then clears out the recently input value on the textbox model
    const addTask = () => {
      //Makes sure that it is not empty
      if (newTask.value.trim() !== ''){
        tasks.value.push(newTask.value);
        newTask.value = '';
      }
    };

    // With parameter index for deleting specific item
    const deleteTask = (index) => {
      //Takes out the value
      tasks.value.splice(index, 1);
    }

    onMounted(async() => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/todos');
        const data = await response.json();
        tasks.value = data.map((task) => task.title);
      } catch (error) {
        console.log('Error fetching tasks');
      }
    });
</script>

<template>
  <h1>Hello {{name}}!</h1>
  <!--Using conditionals here, if status is true = the paragraph will be displayed, else, it will hide-->
  <p v-if="status">User is active</p>
  <!-- Just like the else block-->
  <p v-else>User is inactive</p>

  <!--However if you want conditions that uses string-->
  <p v-if="status_txt === 'active'">User is active (status_txt)</p>
  <!--Using else if-->
  <p v-else-if="status_txt === 'pending'">User is pending (status_txt)</p>
  <p v-else>User is inactive (status_txt)</p>

  <!--Loop through list using v-for-->
  <h3>Tasks:</h3>
  <ul>
    <!--Loop variable task in tasks that was initialized from the data as list-->
    <!--The :key is used in order to get the data just like any list getting the value from the key-->
    <li v-for="(task, index) in tasks" :key="task">
      <!--Adding delete button-->
      <span>
        {{ task }}
      </span>
      <button @click="deleteTask(index)">x</button>
    </li>
  </ul>

  <!--Binding a specific data source using v-bind-->
  <a v-bind:href="link">Click for Google</a><br>

  <!--Shorter way of using bind do not forget the : before href or else it will treat the link literally as set of link not the value we have set-->
  <a :href="link">Click for google (Shorter way)</a><br><br>

  <!--V-on directive calls the method with a button click-->
  <button v-on:click="toggleStatus">Change Status</button>

  <!-- Shorter way of the v-on directive-->
   <!--<button @click="toggleStatus">Change Status</button>-->


   <h1>Sample Form</h1>
   <form @submit.prevent="addTask">
    <label for="newTask">Add Task</label>
    <!--The v-model directive binds the variable we have set from the script setup-->
    <input type="text" id="newTask" name="newTask" v-model="newTask">
    <button type="submit">Submit</button>
   </form>
   
</template>

<!--Refers to adding a style to a particular component-->
<style scoped>

</style>
