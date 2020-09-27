<template>
  <b-navbar type="dark" variant="info">
    <b-navbar-brand href="#">My Album</b-navbar-brand>
    <b-collapse is-nav id="search">
      <b-navbar-nav class="ml-auto">
        <b-form-input placeholder="Search" v-model="word"/>
        <b-button @click="search">Search</b-button>
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</template>

<script>
export default {
  data(){
    return{
      word:''
    }
  },
  methods:{
    search(){
      this.$emit('search', this.word)
    }
  }
}
</script>