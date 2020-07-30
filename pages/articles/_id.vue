<template>
  <div class="container">{{ $route.params.id }}</div>
</template>

<script>
export default {
  name: 'Article'
}
</script>

<style lang="postcss" scoped>
.container {
  @apply min-h-screen flex justify-center items-center text-center mx-auto;
}
</style>
