<template>
  <v-ons-page>
    <h2>設定詳細</h2>
    <p style="text-align: center">
      <v-ons-button @click="popPage" style="margin: 6px 0">戻る</v-ons-button>
    </p>
  </v-ons-page>
</template>
<script>
  export default {
    key: 'SettingDetail',
    methods: {
      popPage() {
        this.$emit('pop-page');
      }
    }
  }
</script>
