<template>
  <div class="workout-card">
    <div class="workout-card__header">
      <p class="workout-card__title">{{ workout.workoutName }}</p>
      <radial-progress-bar :progress="calculateProgress()"></radial-progress-bar>
      <p class="workout-card__started-time">{{ formatDate(new Date(workout.startedTime)) }}</p>
    </div>
    <div class="workout-card__exercises">
      <table class="workout-card-exercise">
        <tr>
          <th>Exercise</th>
          <th>Reps</th>
          <th>Series</th>
        </tr>
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
import RadialProgressBar from "./RadialProgressBar.vue";

export default {
  props: ["workout"],
  components: {
    RadialProgressBar
  },
  mounted: function() {
    this.calculateProgress();
  },
  methods: {
    formatDate: date => date.getHours() + ':' + date.getMinutes(),
    calculateProgress: function() {
      const startedTime = new Date(this.workout.startedTime);
      const endTime = new Date(startedTime.getTime() + this.workout.duration * 60000);
      const minutesLeft = (new Date().getTime() - startedTime.getTime()) / 60000;
      const progress = minutesLeft * 100 / this.workout.duration;
      return 100 - progress.toFixed(0);
    }
  }
};
</script>

<style lang="scss">
.workout-card {
  background-color: #eee;
  width: 400px;
  margin: 10px 0 0 10px;
  padding: 5px;

  &__header {
    display: flex;
    justify-content: space-between;
  }

  &__title {
    font-weight: bold;
    font-size: 20px;
  }
}

.workout-card-exercise {
  width: 100%;
}

</style>
