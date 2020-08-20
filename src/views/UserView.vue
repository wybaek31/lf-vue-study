<template>
  <div>
      {{ userId }}
  </div>
</template>

<script>
export default {
    data() { 
        return {
            userId: "",
        }
    },
    created() {
        this.userId = this.$route.params.id;
    }
}
</script>

<style>

</style>