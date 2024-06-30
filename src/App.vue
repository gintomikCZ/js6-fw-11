<template>
  <TYearPicker :step="3" :maxHeight="300" upArrowLabel="up">
    <template v-slot:arrowUp>
      <div>up</div>
    </template>
    <template v-slot:arrowDown>
      <div>down</div>
    </template>
  </TYearPicker>
</template>


<script>
import TYearPicker from '@/components/TYearPicker.vue'
export default {
  name: 'App',
  components: { TYearPicker }
}

</script>
