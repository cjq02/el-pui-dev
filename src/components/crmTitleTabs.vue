<template>
  <div class="crm-title-tabs">
    <div v-for="(item, i) in data" :class="{ active: tabIndex === i }" @click="clickItem(i)">
      {{item}}
    </div>
  </div>
</template>
<script>

export default {
  name: 'CrmTitleTabs',
  model: {
    prop: 'tabIndex',
    event: 'change'
  },
  props: {
    data: {
      type: Array,
      default: () => []
    },
    tabIndex: {
      type: Number,
      default: 0
    }
  },
  methods: {
    clickItem(i) {
      this.$emit('change', i)
    }
  }
}
</script>
<style lang="scss" scoped>
.crm-title-tabs {
  display: flex;
  flex-direction: row;
  padding: 4px;
  border-radius: 4px;
  opacity: 1;
  border: 1px solid #DEE1E7;
  width: fit-content;
  background-color: white;

  div {
    width: 96px;
    height: 32px;
    opacity: 1;
    text-align: center;
    line-height: 32px;
    font-size: 16px;
    color: #606266;
    cursor: pointer;
  }

  .active {
    background: linear-gradient(180deg, #3CA0F6 0%, #3B71E8 100%);
    box-shadow: 0px 0px 5px 1px rgba(0,0,0,0.03);
    border-radius: 2px 2px 2px 2px;
    color: white;
  }
}
</style>
