<template>
	<div class="addBtn" @click="addhandler"> + 添加</div>
</template>
<script type='text/ecmascript-6'>
export default {
  methods: {
    addhandler() {
      this.$emit("addForm");
    }
  }
};
</script>
<style lang='scss' rel="stylesheet/scss" scoped>
@import "@/style/commonStyle.scss";
.addBtn {
  margin-top: 18px;
  height: 38px;
  line-height: 38px;
  text-align: center;
  font-size: 14px;
  color: $font-color-normal;
  background: $btn-color-light;
  border: 1px dashed $border-color-normal;
  cursor: pointer;
  &:hover {
    background: $btn-hover-light;
  }
}
</style>

