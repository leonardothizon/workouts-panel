<template>
  <div class="workout-card">
    <div class="workout-card__header">
      <p class="workout-card__title">{{ workout.workoutName }}</p>
      <p class="workout-card__started-time">{{ workout.startedTime }}</p>
    </div>
    <div class="workout-card__exercises">
      <table class="workout-card-exercise">
        <tr v-for="ex in workout.exercises" :key="ex.id">
          <td>{{ ex.name }}</td>
          <td>{{ ex.reps }}</td>
          <td>{{ ex.series }}</td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  props: ["workout"],
};
</script>

<style lang="scss">
.workout-card {
  background-color: #eee;
  width: 400px;
  margin: 0 10px;
  padding: 5px;

  &__header {
    display: flex;
  }

  &__title {
    font-weight: bold;
    font-size: 20px;
  }
}
</style>
