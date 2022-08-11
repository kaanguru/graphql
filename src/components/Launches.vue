<template>
  <div>
    <h2>👋 Welcome to the SpaceX GraphQL API! 🚀</h2>
    <ApolloQuery :query="require('../graphql/Star.gql')" :variables="{ launches }">
      <template slot-scope="{ result: { loading, error, data } }">
        <!-- Loading -->
        <div v-if="loading" class="loading apollo">Loading...</div>
        <!-- Error -->
        <div v-else-if="error" class="error apollo">An error occured</div>
        <!-- Result -->
        <div v-else-if="data" class="result apollo">
          <div class="launch-item" v-for="item in data.launches" :key="item.id">
            <h5>{{ item.mission_name }}</h5>
          </div>
        </div>
        <!-- No result -->
        <div v-else class="no-result apollo">No result :(</div>
      </template>
    </ApolloQuery>
  </div>
</template>

<script>
export default {
  data() {
    return {
      launches: '',
    }
  },
}
</script>

<style scoped>
.result {
  @apply container mx-auto flex flex-wrap;
}

.launch-item {
  @apply my-2 px-1 mx-auto;
}

h5 {
  @apply px-4 py-2 rounded-full border border-gray-300 text-gray-500 font-semibold text-sm flex w-max cursor-pointer active: bg-gray-300 transition duration-300 ease;
}
</style>
