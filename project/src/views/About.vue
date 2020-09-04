<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

    <div class="card w-50 centrer">
      <div class="card-body">
        <h5 class="card-title">Services</h5>
        <ul>
          <li v-for="service in services" :key="service">
            {{ service }}
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  msg: String,
  data() {
    return {
      services: ["dev"],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  margin: 30px;
}
.centrer {
  margin: auto;
  background: #587e76;
}
.centrerPrim {
  margin: auto;
  background: #f18973;
  height: 50px;
  line-height: 50px;
  text-align: center;
  vertical-align: middle;
}
</style>
