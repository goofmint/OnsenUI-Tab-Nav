<template>
  <v-ons-navigator swipeable
    :page-stack="pageStack"
    @push-page="pushPage"
    @pop-page="popPage"
  ></v-ons-navigator>
</template>

<script>
  import HomeDetail from 'HomeDetail';
  import NewsDetail from 'NewsDetail';
  
  export default {
    data() {
      return {
        pageStack: [this.list]
      };
    },
    props: ['list'],
    methods: {
      popPage() {
        this.pageStack.pop();
        this.$emit('backButton', this.pageStack);
      },
      pushPage(e) {
        if (e.page === 'HomeDetail') e.page = HomeDetail;
        if (e.page === 'NewsDetail') e.page = NewsDetail;
        this.pageStack.push({
          extends: e.page,
          data: () =>  e.data || {}
        });
        this.$emit('backButton', this.pageStack);
      }
    }
  }
</script>
