<template>
  <div class=" min-h-screen flex flex-col m-2 bg-blue-100">
    <div class="text-2xl font-bold">Space X - Graphql APi</div>
    <button
      class="bg-green-500 text-green-100 w-6/12 p-2 my-2 rounded-sm hover:bg-green-600"
      @click="missionLimit = missionLimit + 1"
    >
      Load More Missions
    </button>
    <ul>
      <li v-for="mission in missions" :key="mission.id" class="leading-loose">
        <nuxt-link :to="mission.id"> {{ mission.name }}</nuxt-link>
      </li>
    </ul>
    <div class="bg-white w-full min-h-full flex-grow">
      <nuxt-child :key="$route.params.id"></nuxt-child>
    </div>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  name: 'Home',
  data() {
    return {
      missionLimit: 1
    }
  },
  apollo: {
    missions: {
      query: gql`
        query getMission($limit: Int) {
          missions(limit: $limit) {
            id
            name
          }
        }
      `,
      variables() {
        return {
          limit: this.missionLimit
        }
      }
    }
  }
}
</script>

<style lang="postcss"></style>
