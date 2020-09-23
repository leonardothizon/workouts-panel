<template>
  <main class="workout-viewer">
    <workout-card v-for="workout in workouts" :key="workout.id" :workout="workout" />
  </main>
</template>

<script>
import WorkoutCard from "./WorkoutCard.vue";
import workouts from '../assets/workouts.json';

export default {
  data() {
    return {
      workouts: workouts
    }
  },
  components: {
    WorkoutCard,
  },
};
</script>

<style scoped>
.workout-viewer {
  display: flex;
}
</style>
