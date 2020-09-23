<template>
  <WorkoutViewer />
</template>

<script>
import WorkoutViewer from './components/WorkoutViewer.vue'

export default {
  name: 'App',
  components: {
    WorkoutViewer
  }
}
</script>

<style lang="sass">
  @import 'scss/_reset.scss'
</style>
