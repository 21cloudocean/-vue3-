<template>
  <form class="form-inline" @submit.prevent="onFormSubmit">
    <div class="input-group mb-2 mr-sm-2">
      <div class="input-group-prepend">
        <div class="input-group-text">任务</div>
      </div>
      <input
        type="text"
        class="form-control"
        placeholder="请输入任务信息"
        style="width: 356px"
        v-model.trim="taskname"
      />
    </div>

    <button type="submit" class="btn btn-primary mb-2">添加新任务</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      taskname: ''
    }
  },
  emits: ['add'],
  methods: {
    onFormSubmit() {
      // 1 判断提交的是否为空
      if (!this.taskname) return alert('任务名称不能为空！')
      // 2 触发自定义事件，并向外界传递数据
      // 只传taskname，其余交给App.vue处理，不要在这里就把object写全了
      this.$emit('add', this.taskname)
      // 3 清空文本框
      this.taskname = ''
    }
  }
}
</script>

<style></style>
