
<template>
  <v-data-table
    :headers="headers"
    :items="posts"
    class="elevation-1"
  >
    <template v-slot:items="props">
      <td>{{ props.item.date }}</td>
      <td class="text-xs-right">
        <a :href="props.item.url" target="_blank">{{ props.item.url }}</a></td>
      <td class="text-xs-right">{{ props.item.type }}</td>
      <td class="text-xs-right">{{ props.item.slug }}</td>
      <td class="text-xs-right">{{ props.item.count }}</td>
    </template>
  </v-data-table>
</template>

<script>
  export default {
    data () {
      return {
        headers: [
          { text: 'Date', value: 'date' },
          { text: 'Url', value: 'url', sortable: false },
          { text: 'Type', value: 'type' },
          { text: 'Slug', value: 'slug', sortable: false },
          { text: 'Count', value: 'count' }
        ],
        posts: [
          {
            "url": "https://reblog.kondoumh.com/post/184336135127",
            "date": "2019-04-21 06:52:45 GMT",
            "type": "photo",
            "slug": "基本情報技術者試験受けてくる-和総さんのツイート-基本情報技術者試験受けてくる-から",
            "count": 228
          },
          {
            "url": "https://reblog.kondoumh.com/post/184319291597",
            "date": "2019-04-20 15:01:19 GMT",
            "type": "quote",
            "slug": "2つの事が起きました",
            "count": 1
          },
          {
            "url": "https://reblog.kondoumh.com/post/184003539017",
            "date": "2019-04-07 05:30:32 GMT",
            "type": "photo",
            "slug": "食べてたカップ麺のかやく袋よく見たら縦読み入ってる-4wlclimeさんのツイート",
            "count": 12
          },
          {
            "url": "https://reblog.kondoumh.com/post/183604104417",
            "date": "2019-03-21 08:28:26 GMT",
            "type": "photo",
            "slug": "家人に教えて貰いましたが欧米のexcelマナー講師によれば全てのシートでa1セルにカーソル置いて",
            "count": 5
          },
          {
            "url": "https://reblog.kondoumh.com/post/183599077742",
            "date": "2019-03-21 02:33:54 GMT",
            "type": "quote",
            "slug": "bill",
            "count": 16
          },
          {
            "url": "https://reblog.kondoumh.com/post/183507626102",
            "date": "2019-03-17 02:11:35 GMT",
            "type": "photo",
            "slug": "子桃太郎読んで-親昔々あるところに-子もっとスターウォーズっぽく",
            "count": 2
          },
          {
            "url": "https://reblog.kondoumh.com/post/183350324742",
            "date": "2019-03-10 05:21:53 GMT",
            "type": "photo",
            "slug": "おおおおおおこうしてみるとgoogle翻訳が進化してるぅぅぅぅ",
            "count": 1
          },
          {
            "url": "https://reblog.kondoumh.com/post/182862550052",
            "date": "2019-02-17 06:22:41 GMT",
            "type": "quote",
            "slug": "オレ-オマエ-ゲンシジンスル-プログラム-カイタ-ゲンシジン-ジョシ-ツカワナイ-ゲンゴショリ-スル",
            "count": 5
          },
          {
            "url": "https://reblog.kondoumh.com/post/182859251837",
            "date": "2019-02-17 02:57:07 GMT",
            "type": "quote",
            "slug": "ソフトウェア業界はpcと電気代があれば開発ができるという意味ではかなり金が掛からない業界であり際限",
            "count": 44
          },
          {
            "url": "https://reblog.kondoumh.com/post/182574685722",
            "date": "2019-02-05 08:19:27 GMT",
            "type": "quote",
            "slug": "契約書って何で甲と乙と丙なんですかね無駄に難しく感じるので俺とお前と大五郎くらいにできないものだろ",
            "count": 1
          },
          {
            "url": "https://reblog.kondoumh.com/post/182519192757",
            "date": "2019-02-03 07:38:13 GMT",
            "type": "quote",
            "slug": "パソコンにデータ突っ込んで特徴みつけるのがmachine-learning-machine",
            "count": 15
          },
        ]
      }
    }
  }
</script>

<style>

</style>
