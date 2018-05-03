<template>
  <div>
      <component
        v-for="(component, index) in view.components" 
        :is="component.name"
        :props="component.props"
        :events="component.events"
        :key="index"
        @input="component.props.value = $event"
        ></component>
        {{$data}}
  </div>
</template>

<script>
export default {
  data() {
    return {
      view: []
    }
  },
  mounted() {
    this.view = {
      components: [
        {
          name: 'input-app', 
          events: [{type:'input'}],
          props: {
            type: 'email', 
            value:'hola@hola.es'
          }
        }
      ]
    }
  }
}
</script>
