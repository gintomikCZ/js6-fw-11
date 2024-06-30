<template>
  <div class="container">
    <div @click="onClick">{{ startYear }}</div>
    <div v-if="show" class="years-container">
      <div class="arrows" @click="onArrowUpClick">
        <slot name="arrowUp"></slot>
      </div>
      <ul :style="{ maxHeight: maxHeight + 'px' }">
        <li v-for="year in years">{{ year }}</li>
      </ul>
      <div class="arrows" @click="onArrowDownClick">
        <slot name="arrowDown"></slot>
      </div>
    </div>
  </div>
</template>


<script>

export default {
  name: 'App',
  props: {
    startYear: {
      type: Number,
      default: () => {
        const today = new Date()
        return today.getFullYear()
      },
    },
    // upArrowLabel: {
    //   type: String,
    //   default: 'vrchní'
    // },
    maxHeight: {
      type: Number,
      default: 200
    },
    step: {
      type: Number,
      default: 5
    }
  },
  data () {
    return {
      show: false,
      // years: [],
      down: 0,
      up: 0
    }
  },
  // created () {
  //   for(let i = -5; i < 6; i++) {
  //     this.years.push(this.startYear + i)
  //   }
  // },
  computed: {
    years () {
      const ar = []
      for(let i = -this.step - this.up * this.step; i < (this.step + 1) + this.down * this.step; i++) {
        ar.push(this.startYear + i)
      }
      return ar
    }
  },
  methods: {
    onClick () {
      this.show = !this.show
      if (!this.show) {
        this.up = 0;
        this.down = 0;
      }
    },
    onArrowDownClick () {
      // const lastYear = this.years[this.years.length - 1]
      // for (let i = 1; i <=5 ; i++) {
      //   this.years.push(lastYear + i)
      // }
      this.down += 1
    },
    onArrowUpClick () {
      // const firstYear = this.years[0]
      // for (let i = 1; i <=5 ; i++) {
      //   this.years.unshift(firstYear - i)
      // }
      this.up += 1
    }
  }
}


</script>

<style>
.container {
  position: relative
}
ul {


  list-style-type: none;

  padding: 0;


  max-height: 200px;
  overflow: auto;
}
li, .arrows {
  padding: .35em .7em;
  text-align: center;
}
.arrows {
  background: lightgreen;
  cursor: pointer
}
.years-container {
  width: 100px;
  display: flex;
  flex-direction: column;
  position: absolute;
  transform: translateY(-50%);
  left: calc(100% + 1rem);
  border: 1px solid #cdcdcd;
}
</style>

