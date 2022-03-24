<template>
  <div class="about">
    <h1>This is an about page</h1>
    {{ ime }}
    {{ sha }}
    <router-view />
  </div>
</template>
<script>
export default {
  props:["sha"],
  data() {
    return {
      ime: "OK"
    };
  },
  name: "AboutPage",
};
</script>

