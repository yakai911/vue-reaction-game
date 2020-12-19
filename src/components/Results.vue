<template>
  <p>你本次的反应时间是:{{ score }} ms</p>
  <h3>
    恭喜你，你获得了<b style="text-decoration: underline">{{ rank }}</b
    >的称号
  </h3>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      rank: null,
    };
  },
  mounted() {
    if (this.score < 250) {
      this.rank = "金手指";
    } else if (this.score < 400) {
      this.rank = "银手指";
    } else if (this.score < 650) {
      this.rank = "铜手指";
    } else {
      this.rank = "断手指";
    }
  },
  unmounted() {
    this.rank = null;
  },
};
</script>

<style>
</style>