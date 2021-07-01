<template>
  <div class="content"></div>
</template>

<script>

export default {
  created() {
    Axios.get("https://coolsacademy.herokuapp.com/api/courses").then(response => console.log(response))
}
};
</script>

<style scoped lang="scss">
</style>