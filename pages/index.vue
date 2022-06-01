<template>
  <div>
    <img :src="response.details.ext_1.url" width="800">
    <div>{{response.details.ext_2}}</div>
    <div>{{response.details.ext_3}}</div>

    <div v-for="n in response.details.ext_4" :key="n.slag" >
      <img :src="n.ext_4.url" width="400">
      <div>{{ n.ext_3 }}</div>
      <div>{{ n.ext_5 }}</div>
      <div>{{ n.ext_s6 }}</div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $axios}) {
    try {
      const response = await $axios.$get(
        process.env.BASE_URL + '/rcms-api/3/service/3'
        )
        console.log(response.details.ext_1.url)
        return { response }
        } catch (e) {
          console.log("ERROR while getting response: ", e.message)
          }
  },
}
</script>