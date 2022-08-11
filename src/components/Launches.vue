<template>
  <div>
    <h2>SpaceX Launches from GraphQL API!🚀</h2>
    <img src="icons8_drag_100px.png" alt="drag" class="w-10 h-10  mx-auto animate-bounce">
    <p v-if="date !== ''">Date of Dragged Launch <span class="text-rose-900 ">{{ mission }}</span> is: {{ date }} </p>
    <p v-else>Just Drag Launches to see launch date</p>

    <ApolloQuery :query="require('../graphql/Star.gql')" :variables="{ launches }">
      <template slot-scope="{ result: { loading, error, data } }">
        <!-- Loading -->
        <div v-if="loading" class="loading ">Loading...</div>
        <!-- Error -->
        <div v-else-if="error" class="error ">An error occured</div>
        <!-- Result -->
        <div v-else-if="data" class="results ">
          <draggable v-model="data.launches" class="draggable" :move="checkMove" @start="drag = true" @end="drag = false">
            <h5 v-for="element in data.launches" :key="element.mission_id[0]">{{ element.mission_name }} <img src="icons8_drag_100px.png" class="ml-3 w-5 h-5"> </h5>
          </draggable>
        </div>
        <!-- No result -->
        <div v-else class="no-result ">No result 😒 yet...</div>
      </template>
    </ApolloQuery>
  </div>
</template>

<script>
import draggable from 'vuedraggable'
export default {
  components: {
    draggable,
  },
  data() {
    return {
      launches: '',
      date: "",
      mission: ""
    }
  },
  methods: {
    checkMove(evt) {
      this.date = (evt.draggedContext.element.launch_date_local).slice(0, 10);
      this.mission = (evt.draggedContext.element.mission_name);
    }
  },

}
</script>

<style scoped>
.results {
  @apply container mx-auto;
}

h2 {
  font-family: 'Rubik Dirt', cursive;
  @apply text-rose-400 text-4xl tracking-widest;
}

p {
  @apply text-lg font-bold animate-pulse;
}

.draggable {
  @apply flex flex-wrap;

}

h5 {
  @apply m-3 px-4 py-2 rounded-full border border-rose-600 text-red-800;
  @apply bg-light-300 shadow-light-700 drop-shadow-md;
  @apply font-semibold text-sm flex w-max cursor-pointer active: bg-gray-300 transition duration-300 ease;
}
</style>
