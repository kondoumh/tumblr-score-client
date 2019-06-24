
<template>
  <v-data-table
    :headers="headers"
    :items="posts"
    class="elevation-1"
  >
    <template v-slot:items="props">
      <td>{{ props.item.date.substring(0, 19) }}</td>
      <td class="text-xs-left">
        <a :href="props.item.url" target="_blank">{{ props.item.slug ? props.item.slug : props.item.url }}</a></td>
      <td class="text-xs-right">{{ props.item.type }}</td>
      <td class="text-xs-right">{{ props.item.count }}</td>
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
      headers: [
        { text: 'Date', value: 'date' },
        { text: 'Slug', value: 'slug', sortable: false },
        { text: 'Type', value: 'type' },
        { text: 'Count', value: 'count' }
      ]
    })
  }
</script>

<style>

</style>
