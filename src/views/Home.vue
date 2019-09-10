<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld :str="str" @setValue="getValue"></HelloWorld>
    <h1>{{value}}</h1>
    <h2>{{info.title}}</h2>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "home",
  data() {
    return {
      value: [],
      str: {
        name: "hello",
        age: 12,
        last: "父向子传值"
      },
      info: [],
    };
  },
  components: {
    HelloWorld
  },
  methods: {
    getValue(value) {
      this.value = value;
    }
  },
  mounted() {
    this.$axios
    .get('http://jsonplaceholder.typicode.com/posts')
    .then((response) => {
      console.log(response);
      var data = response.data[0];
      console.log(data);
      this.info = data;
      console.log(this);
    })
    .catch(function(error){
      console.log(error);
    })
  },
};
</script>
