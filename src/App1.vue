<template>
  <!-- <ul>
    <li v-for="item in arrToDisplay">{{ item }}</li>
  </ul> -->
  <!-- <ul>
    <template v-for="(item, index) in arr" :key="'itemNo' + index">
      <li v-if="index + 1 <= itemsToDisplay">{{ item }}</li>
    </template>
  </ul> -->
  <ul>
    <li v-for="n in itemsToDisplay">{{ arr[offset + n - 1] }}</li>
  </ul>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      arr: [1, 8, 9, 5, 6, 5, 7],
      offset: 2,
      itemsToDisplay: 5
    }
  },
  computed: {
    arrToDisplay () {
      const arr = []
      for(let i = 0; i < this.itemsToDisplay; i++) {
        arr.push(this.arr[i])
      }
      return arr
    }
  }
}


</script>