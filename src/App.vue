<template>
  <div id="app">
    <Timeline v-bind:data="data"/>
  </div>
</template>

<script>
import Timeline from './components/Timeline'

export default {
  name: "app",
  components: {
    Timeline
  },
  data: function() {
    return {
      data: [
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        },
        {
          date: "20-08-19",
          title: "Titulo 1",
          description: "Lorem Lorem ips sum misl lor",
          icon: ""
        }
      ]
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
