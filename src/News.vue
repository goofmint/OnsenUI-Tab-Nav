<template>
  <v-ons-page>
    <p style="text-align: center">
      Some news here. <br />
      <v-ons-button @click="pushPage" style="margin: 6px 0">詳細画面へ</v-ons-button>
    </p>
  </v-ons-page>
</template>

<script>
import NewsDetail from './NewsDetail';
export default {
  key: 'HomeMaster',
  methods: {
    pushPage(e) {
      this.$emit('push-page', {page: NewsDetail});
    }
  }
}
</script>