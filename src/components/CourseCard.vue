<template>
  <div id="crs">
    <h3>Course: {{ name }} ({{ numCredits }} credits)</h3>
    <br/>
    <h4>Meetings at: </h4>
    <p v-for="(t,pos) in meetings" :key="pos">{{ t }}</p>
  </div>
</template>

<script lang="ts">
    import { Vue, Component, Prop } from "vue-property-decorator";

    @Component
    export default class CourseCard extends Vue {
        @Prop() readonly name!: string;
        @Prop() readonly numCredits!: number;
        @Prop() readonly meetings!: string[];
    }
</script>

<style>
#crs {
  display: inline-block;
  border: 2px solid hsl(30, 90%, 50%);
  border-radius: 0.5em;
  padding: 1em;
  margin: 0.6em;
  box-shadow: 3px 5px 6px 7px hsla(30, 55%, 50%, 0.4);
}
</style>