<template>
  <div id="app">
    <h2>Personal Info</h2>
    Name: {{ myInfo.name }}
    <br/>
    Semester: {{ myInfo.semester }} {{ myInfo.year }}
    <br/>

    Courses
    <ol>
      <li v-for="(c,pos) in myInfo.courses" :key="pos">
        {{ c.name }} ({{ c.credits }} credits)
      </li>
    </ol>

    <table>
      <tr>
        <th>Course</th>
        <th>Credits</th>
      </tr>
      <tr v-for="(c,pos) in myInfo.courses" :key="pos">
        <td>{{ c.name }}</td>
        <td class="center">{{ c.credits }}</td>
      </tr>
    </table>

    <CourseCard 
      v-for="(c,pos) in myInfo.courses" 
      :key="pos" 
      v-bind:name="c.name" 
      v-bind:num-credits="c.credits"
      v-bind:meetings="c.meetings"
    ></CourseCard>
    <!-- <hello-world msg="Welcome to Your Vue.js + TypeScript App"/> -->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';
import CourseCard from './components/CourseCard.vue';

@Component({
  components: {
    HelloWorld,
    CourseCard,
  },
})
export default class App extends Vue {
  readonly myInfo = {
    name: "Adam Chlebek",
    semester: "Winter",
    year: 2021,
    courses: [
      {
        name: "CIS 371 Web Application Programming",
        credits: 3,
        meetings: ["Mon 12p-12:50p", "Wed 12p-12:50p", "Fri 12p-12:50p"]
      },
      {
        name: "CIS 452 Operating Systems Concepts",
        credits: 4,
        meetings: ["Thu 12p-1:50p"]
      },
      {
        name: "CIS 467 Computer Science Project",
        credits: 4,
        meetings: ["Tue 6a-7:50a", "Thu 6a-7:50a"]
      },
      {
        name: "GEO 111 Exploring The Earth",
        credits: 4,
        meetings: ["None"]
      }
    ]
  };
}
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    margin-top: 60px;
  }

  table, th, td {
    border: 1px solid black;
  }

  .center {
    text-align: center;
  }
</style>
