<template>
  <v-ons-page>
    <p style="text-align: center">
      Welcome home!<br />
      <v-ons-button @click="pushPage" style="margin: 6px 0">詳細画面へ</v-ons-button>
    </p>
  </v-ons-page>
</template>
<script>
import HomeDetail from './HomeDetail';
export default {
  key: 'HomeMaster',
  methods: {
    pushPage(e) {
      this.$emit('push-page', {page: HomeDetail});
    }
  }
}
</script>
