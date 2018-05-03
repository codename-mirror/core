<template>
  <span>
     <input
     ref="input"
     :type="type"
     :disabled="disabled"
     v-model="value"
     >
  </span>
</template>

<script>
export default {
  props: {
      props: {type: Object},
      events: {type: Array | Object}
  },
  data() {
      return {
          type: null,
          disabled: null,
          value: null
      }
  },
  methods:{
      setEvent(event) {
          setTimeout(()=> this.$refs.input.addEventListener(event.type, e => {
              if(event.type == 'input') this.$emit('input', this.value)
              else if(event.type == 'click') this.$emit('click')
          }), 100)
      }
  },
  mounted() {
      this.value = this.props.value
      this.type = this.props.type || 'text';
      this.disabled = this.props.disabled || false
      
      this.events.forEach(event => this.setEvent(event))
  },
}
</script>

