<template>
  <v-ons-page>
    <h2>ホーム詳細</h2>
    <p style="text-align: center">
      <v-ons-button @click="popPage" style="margin: 6px 0">戻る</v-ons-button>
      <v-ons-button @click="toNewsDetail" style="margin: 6px 0">ニュース詳細へ</v-ons-button>
    </p>
  </v-ons-page>
</template>
<script>
  export default {
    key: 'HomeDetail',
    methods: {
      popPage() {
        this.$emit('pop-page');
      },
      toNewsDetail() {
        this.$emit('push-page', {page: 'NewsDetail'});
      }
    }
  }
</script>
