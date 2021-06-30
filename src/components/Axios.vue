<template>
  <div class="content"></div>
</template>

<script>

export default {
  created() {
    Axios.get("http://127.0.0.1:8000/api/courses").then(response => console.log(response))
}
};
</script>

<style scoped lang="scss">
</style>