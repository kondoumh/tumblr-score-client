
<template>
  <v-data-table
    :headers="headers"
    :items="posts"
    :items-per-page="itemsPerPage"
    :footer-props="{
      'items-per-page-options': [5, 10, 15, 20, 25, 30]
    }"
    class="elevation-1"
  >
    <template v-slot:item.date="{ item }">
      {{ item.date.substring(0, 19) }}
    </template>
    <template v-slot:item.slug="{ item }">
      <a :href="item.url" target="_blank">{{ item.slug ? item.slug : item.url }}</a>
    </template>
  </v-data-table>
</template>

<script>
  export default {
    async mounted () {
      this.fetchData()
    },
    methods: {
      async fetchData () {
        const res = await fetch(this.url)
        const json = await res.json()
        this.posts = json
      }
    },
    computed: {
      url: () => 'https://compassionate-thompson-b0de67.netlify.com/tumblr-score.json'
    },
    data: () => ({
      posts: [],
      itemsPerPage: 5,
      headers: [
        { text: 'Date', value: 'date' },
        { text: 'Slug', value: 'slug', sortable: false },
        { text: 'Type', value: 'type' },
        { text: 'Count', value: 'count' }
      ],
    })
  }
</script>

<style>

</style>
