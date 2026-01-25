<script>
// we will do the options API first then convert into composition API later on
export default{
  data(){
    return{
      name: 'Angel',
      status: true, //This is boolean
      status_txt: 'active',
      tasks: ['Task One', 'Task Two', 'Task Three'],
      link: 'https://google.com', 
    };
  },
  methods: {
    toggleStatus(){
      if(this.status_txt === 'active'){
        this.status_txt = 'pending';
      }
      else if(this.status_txt === 'pending'){
        this.status_txt = 'inactive';
      }
      else{
        this.status_txt = 'active';
      };
    },
  }
};
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
    <li v-for="task in tasks" :key="task">{{ task }}</li>
  </ul>

  <!--Binding a specific data source using v-bind-->
  <a v-bind:href="link">Click for Google</a><br>

  <!--Shorter way of using bind do not forget the : before href or else it will treat the link literally as set of link not the value we have set-->
  <a :href="link">Click for google (Shorter way)</a><br><br>

  <!--V-on directive calls the method with a button click-->
  <button v-on:click="toggleStatus">Change Status</button>

  <!-- Shorter way of the v-on directive-->
   <!--<button @click="toggleStatus">Change Status</button>-->
</template>

<!--Refers to adding a style to a particular component-->
<style scoped>

</style>
