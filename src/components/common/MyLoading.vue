<template>
  <van-popup v-model="show" :close-on-click-overlay="false" class="ui-inner-loading-dialog">
    <van-loading color="white" class="ui-inner-loading-spin"/>
    <div class="ui-inner-loading-text">{{loadingMsg}}</div>
  </van-popup>
</template>

<script>
import Vue from "vue";
import { mapState, mapActions, mapMutations, mapGetters } from "vuex";
import { Popup, Loading } from "vant";
Vue.use(Popup).use(Loading);
export default {
  name: "Loading",
  computed: {
    ...mapState("common", ["loadingCount", "loadingMsg"]),
    show: {
      get: function() {
        return this.loadingCount > 0;
      },
      set: function() {}
    }
  }
};
</script>

<style lang="scss">
.ui-inner-loading-dialog {
  padding-top: 15px;
  padding-bottom: 15px;
  padding-left: 25px;
  padding-right: 25px;
  background-color: hsla(0, 0%, 10%, 0.5) !important;
  border-radius: 5px;
}
.ui-inner-loading-spin {
  display: block !important;
  margin: 0 auto !important;
}
.ui-inner-loading-text {
  color: #eee;
  margin-top: 5px;
  font-size: 14px;
}
</style>
