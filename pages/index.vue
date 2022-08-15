<template>
  <div>
    <img src="~/assets/logo.svg" />
    <ul v-for="mountain in mountains" :key="mountain.id">
      <NuxtLink :to="`${mountain.continent.toLowerCase()}/${mountain.slug}`">
        <li>{{ mountain.title }}</li>
      </NuxtLink>
    </ul>
  </div>
</template>
<script>
export default {
  async asyncData() {
    const mountains = await fetch(
      'https://api.nuxtjs.dev/mountains'
    ).then((res) => res.json())
    console.log(mountains)
    return { mountains }
  }
}
</script>
<style>
img {
  width: 20vw;
  height: 15vw;
}
</style>