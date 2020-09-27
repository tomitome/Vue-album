<template>
  <b-card no-body style="max-width:320px;">
    <b-card-body>
      <b-card-title>{{pic.tags}}</b-card-title>
      <b-img :src="pic.webformatURL" fluid thumbnail />
    </b-card-body>
  </b-card>
</template>

<script>
export default {
  props:['pic']
}
</script>