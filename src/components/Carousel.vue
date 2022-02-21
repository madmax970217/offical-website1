<template>
  <div>
    <el-carousel height="320px">
      <el-carousel-item v-for="item in articleData" :key="item.moduleId">
        <img :src="item.pic" alt="" />
        <div class="title">
          <h1>{{ item.title }}</h1>
        </div>
      </el-carousel-item>
    </el-carousel>
  </div>
</template>
<script>
export default {
  data: function() {
    return {
      articleData: [],
    };
  },
  mounted: function() {
    this.fetchData();
  },
  methods: {
    fetchData: function() {
      var _this = this;
      this.$http
        .get("/src/data/catetoryCarousel.data")
        .then(function(res) {
          _this.articleData = res.data;
        })
        .catch(function(err) {
          console.log("请求轮播图数据出错");
        });
    },
  },
};
</script>
<style scoped>
.el-carousel__item img {
  width: 100%;
  height: 100%;
}
.title {
  position: absolute;
  left: 20%;
  top: 35%;
  z-index: 9999;
  color: aliceblue;
}
</style>
