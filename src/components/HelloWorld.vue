
<template>
  <v-card>
    <v-card-title>
      reblog.kondoumh.com
      <v-spacer/>
      <v-btn icon color="gray" v-on:click="fetchData">
        <v-icon>mdi-cached</v-icon>
      </v-btn>
      <v-spacer/>
      {{ date }}
    </v-card-title>
    <v-card-title>
      <v-select v-model="type" :items="types" label="type" />
      <v-spacer />
      <v-text-field v-model="note_count" type="number" label="More than" />
      <v-spacer />
      <v-text-field v-model="search" append-icon="mdi-magnify" label="Search" />
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="posts"
      :search="search"
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
        <a :href="item.post_url" target="_blank">{{ item.slug ? item.slug : item.id_string }}</a>
      </template>
    </v-data-table>
  </v-card>
</template>

<script>
  export default {
    async mounted () {
      this.fetchData()
    },
    methods: {
      async fetchData () {
        const res = await fetch('https://tmblrscore-kondoumh.netlify.app/posts.json', {
          mode: 'cors',
        })
        const json = await res.json()
        this.posts = json.posts
        this.date = json.date
      }
    },
    computed: {
      headers() {
        return [
          { text: 'Date', value: 'date', filter: () => true },
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
            value: 'note_count',
            filter: value => {
              if (!this.note_count) return true
              return value > parseInt(this.note_count)
            }
          }
        ]
      },
    },
    data: () => ({
      posts: [],
      date: '',
      search: '',
      types: ['', 'quote', 'photo', 'text', 'link'],
      type: '',
      note_count: '',
      itemsPerPage: 5,
    })
  }
</script>

<style>

</style>
