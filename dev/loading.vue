<template lang="pug">
.container
  a(href="https://vue-comps.github.io/vue-clusterize/blob/master/dev/loading.vue") source
  p 0.5 sec delay for data
  clusterize(v-ref:clusterize @get-data="getData" @get-data-count="getDataCount" v-bind:height="400" v-bind:style="{width:'200px'}")
    div.clusterize-row(v-if="!loading") {{data}}
    p(slot="loading") loading
</template>

<script lang="coffee">
module.exports =
  components:
    "clusterize": require "../src/clusterize.vue"
  data: ->
    rowsData: (x for x in [1..10000])
  methods:
    getData: (first,last,cb) ->
      setTimeout((=>
        cb(@rowsData[first..last])),500)
    getDataCount: (cb) ->
      setTimeout((=>
        cb(@rowsData.length)),500)
</script>

<style lang="stylus">
.clusterize
  border 1px solid black
.container
  height:100%
  width:100%
.container > a
  position absolute
  left 250px
  top 40px

</style>
