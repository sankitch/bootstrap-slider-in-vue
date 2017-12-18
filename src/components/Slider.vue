<template>
  <div>
    <input
      id="ex1"
      type="text"
      data-slider-id="ex1Slider"
      :data-slider-step="step"
      :data-slider-min="min"
      :data-slider-max="max"
      :data-slider-value="value"
      />
    <input v-model="value" type="number" :min="min" :max="max" :step="step">
  </div>
</template>

<script>
  import Slider from 'bootstrap-slider'

  export default {
    name: 'slider',
    props: {
      defaultValue: {
        type: Number,
        default: 14
      },
      max: {
        type: Number,
        default: 20
      },
      min: {
        type: Number,
        default: 0
      },
      step: {
        type: Number,
        default: 1
      }
    },
    data () {
      return {
        value: 0,
        slider: null
      }
    },
    mounted () {
      this.slider = new Slider('input#ex1')
      if (this.defaultValue) {
        this.value = this.defaultValue
      }

      this.slider.setValue(this.value)
      this.slider.on('change', this.slideChange)
    },
    methods: {
      slideChange (e) {
        this.value = this.slider.getValue()
      }
    },
    watch: {
      value () {
        this.slider.setValue(this.value)
      }
    }
  }
  </script>

<style lang="scss">
  @import "~bootstrap-slider/src/sass/bootstrap-slider.scss"
</style>
