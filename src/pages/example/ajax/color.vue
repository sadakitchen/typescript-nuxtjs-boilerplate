<template lang="pug">
section.container
  h1.title
    | color
  div
    span color
    span |
    span
      nuxt-link(to="/example/ajax/schema") schema
  div
    img(:src="data.image.named")
  nuxt-link(to="/example/")
    | example top
</template>

<script lang="ts">
import axios from 'axios'
import { Component, Vue } from 'nuxt-property-decorator'

@Component
export default class extends Vue {
  async asyncData() {
    const hex = Math.floor(Math.random() * 16777215).toString(16)
    const { data } = await axios.get(`http://www.thecolorapi.com/id?hex=${hex}`)
    return { data }
  }

  public head() {
    return {
      title: 'ajax/color'
    }
  }
}
</script>
