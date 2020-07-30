<template>
  <div>
    <div v-if="!$apollo.loading">
      <h1>{{ mission.name }}</h1>
      <p>{{ mission.description }}</p>
      <a :href="mission.wikipedia" target="blank">read on wikipedia</a>
    </div>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import gql from 'graphql-tag'
export default {
  name: 'Mission',
  fetch({ redirect, route }) {
    if (!route.params.id) {
      redirect('/9D1B7E0')
    }
  },
  //   data() {
  //     return {
  //       id: '9D1B7E0'
  //     }
  //   },
  apollo: {
    mission: {
      query: gql`
        query getMission($id: ID!) {
          mission(id: $id) {
            id
            name
            wikipedia
            description
          }
        }
      `,
      variables() {
        return {
          id: this.$route.params.id
        }
      }
    }
  }
}
</script>

<style lang="scss" scoped></style>
