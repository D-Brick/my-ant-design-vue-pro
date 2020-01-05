<template>
  <div>
    <a-drawer
      :placement="placement"
      :closable="false"
      :visible="visible"
      @close="onClose"
      width="300px"
    >
      <template v-slot:handle>
        <div class="handle" @click="visible = !visible">
          <a-icon :type="visible ? 'close' : 'setting'"></a-icon>
        </div>
      </template>
      <div>
        <h1>配置主题颜色</h1>
        <a-radio-group 
          :value="$route.query.navTheme || 'dark'"
          @change="(e) => handleSettingChange('navTheme', e.target.value)"
        >
          <a-radio value="dark">黑色</a-radio>
          <a-radio value="light">白色</a-radio>
        </a-radio-group>
        <h1>配置导航样式</h1>
        <a-radio-group
          :value="$route.query.navLayout || 'left'"
          @change="(e) => handleSettingChange('navLayout', e.target.value)">
          <a-radio value="left">左边</a-radio>
          <a-radio value="top">顶部</a-radio>
        </a-radio-group>
      </div>
    </a-drawer>
  </div>
</template>

<script>
export default {
  name: 'SettingDrawer',
  data() {
    return {
      visible: false,
      placement: 'right',
    };
  },
  methods: {
    onClose() {
      this.visible = false;
    },
    handleSettingChange(type, value) {
      this.$router.push({ query: { ...this.$route.query, [type]: value}});
    },
  }
};
</script>

<style scoped>
.handle {
  position: absolute;
  top: 240px;
  right: 300px;
  
  width: 48px;
  height: 64px;
  border-radius: 3px 0 0 3px;

  background: #1890ff;
  text-align: center;
  line-height: 64px;
  font-size: 20px;
  color: #fff;
}
</style>