<template>
  <div class="header">
    <el-input
      v-model="input"
      placeholder="请输入内容"
      prefix-icon="el-icon-search"
    ></el-input>
    <div class="tabs-wrap">
      <!-- <Tabs :tabs="tabs" /> -->
      <div
        class="tab-item"
        v-for="(item, index) in tabs"
        :key="index"
        @click="jump(index)"
      >
        {{ item }}
      </div>
    </div>
    <toggle :show.sync="isVedioShow">
      <More :isShow="isVedioShow" @changeShow="isVedioShow = !isVedioShow" />
    </toggle>
  </div>
</template>

<script>
import More from "@/components/more";
export default {
  name: "Header",
  components: {
    More,
  },
  data() {
    return {
      input: "",
      tabs: ["首页", "留言板", "游戏", "一封信"],
      isVedioShow: false,
    };
  },
  methods: {
    jump(index) {
      switch (index) {
        case 0:
          this.$router.push("/");
          break;
        case 1:
          this.$router.push("/messageboard");
          break;
        case 2:
          this.$router.push("/tetris");
          break;
        case 3:
          this.isVedioShow = !this.isVedioShow;
          break;
        default:
          break;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.header {
  width: 100%;
  height: 15%;
  // background: pink;
  z-index: $header-z-index;
  position: absolute;
  top: 0;
  display: flex;
  align-items: center;
  // justify-content: space-around;
  // background: linear-gradient(45deg, rgba(#bdc3c7, 0.3), rgba(#000, 0.3));
  /deep/.el-input {
    width: 200px;
    border-radius: 999px;
    overflow: hidden;
    margin-left: 10%;

    .el-input__inner {
      // border-bottom: solid #0067c0 2px;
      border: none;
      &:focus {
        border: none;
      }
    }
  }

  .tabs-wrap {
    display: flex;
    font-size: 20px;
    position: absolute;
    right: 15%;
    .tab-item {
      padding: 10px 20px;
      cursor: pointer;
      border-radius: 5px;
      &:hover {
        background: rgba($color: #000000, $alpha: 0.3);
      }
    }
  }
}
</style>