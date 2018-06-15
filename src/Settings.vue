<template>
  <v-ons-page>
    <p style="text-align: center">
      Change the settings. <br />
      <v-ons-button @click="pushPage" style="margin: 6px 0">詳細画面へ</v-ons-button>
    </p>
  </v-ons-page>
</template>

<script>
import SettingDetail from './SettingDetail';
export default {
  key: 'Settings',
  methods: {
    pushPage(e) {
      this.$emit('push-page', {page: SettingDetail});
    }
  }
}
</script>