<template>
  <v-ons-page>
    <h2>ニュース詳細</h2>
    <p style="text-align: center">
      <v-ons-button @click="popPage" style="margin: 6px 0">戻る</v-ons-button>
      <v-ons-button @click="toHomeDetail" style="margin: 6px 0">ホーム詳細へ</v-ons-button>
    </p>
  </v-ons-page>
</template>
<script>
  export default {
    key: 'NewsDetail',
    methods: {
      popPage() {
        this.$emit('pop-page');
      },
      toHomeDetail() {
        this.$emit('push-page', {page: 'HomeDetail'});
      }
    }
  }
</script>
