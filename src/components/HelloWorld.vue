
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
    <template v-slot:body.append>
      <tr>
        <td colspan="2"></td>
        <td>
          <v-select v-model="type" :items="types" label="type"></v-select>
        </td>
        <td>
          <v-text-field v-model="count" type="number" label="More than"></v-text-field>
        </td>
      </tr>
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
      url: () => 'https://compassionate-thompson-b0de67.netlify.com/tumblr-score.json',
      headers() {
        return [
          { text: 'Date', value: 'date', filterable: false },
          { text: 'Slug', value: 'slug', sortable: false },
          {
            text: 'Type',
            value: 'type',
            filter: value => {
              if (!this.type) return true
              return this.type.startsWith(value)
            }
          },
          {
            text: 'Count',
            value: 'count',
            filter: value => {
              if (!this.count) return true
              return value > parseInt(this.count)
            }
          }
        ]
      },
    },
    data: () => ({
      posts: [],
      types: ["", "quote", "photo", "text", "link"],
      type: "",
      count: "",
      itemsPerPage: 5,
    })
  }
</script>

<style>

</style>
