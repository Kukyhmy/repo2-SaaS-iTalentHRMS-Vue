<template>
<div class="app-breadcrumb">
  微启明创网络商务中心    新一代 HR SaaS 组织人才管理平台<span class="breadBtn">Version-1.0</span>
</div>
</template>

<script>
import {generateTitle} from '@/utils/i18n'

export default {
  created() {
    this.getBreadcrumb()
  },
  data() {
    return {
      levelList: null
    }
  },
  watch: {
    $route() {
      this.getBreadcrumb()
    }
  },
  methods: {
    generateTitle,
    getBreadcrumb() {
      let matched = this.$route.matched.filter(item => item.name)
      const first = matched[0]
      if (first && first.name !== 'dashboard') {
        matched = [{path: '/dashboard', meta: {title: 'dashboard'}}].concat(
          matched
        )
      }
      this.levelList = matched
    }
  }
}
</script>

<style rel="stylesheet/scss" lang="scss" scoped>
.app-breadcrumb {
  display: inline-block;
  font-size: 18px;
  line-height: 50px;
  margin-left: 10px;
  color: #ffffff;
  cursor: text;
  // .breadBtn{background: #84a9fe; font-size: 14px ;padding:0 10px;display: inline-block;height: 30px; line-height: 30px;border-radius: 10px; margin-left: 15px;}
   .breadBtn{background: #08a694; font-size: 14px ;padding:0 10px;display: inline-block;height: 30px; line-height: 30px;border-radius: 10px; margin-left: 15px;}
}
</style>
