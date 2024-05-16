<template>
 <div class="header">
    <div class="title">
      <span>YT-UI演练场</span>
    </div>
    <div>
      <span class="ml20">
        显示编译输出: <tiny-switch v-model="state.showCompileOutput" />
      </span>
      <span class="ml20">
        显示ImportMap: <tiny-switch v-model="state.showImportMap" />
      </span>
      <span class="ml20">
        布局方向: <tiny-button-group :data="state.layoutOptions" v-model="state.layout"></tiny-button-group>
      </span>
      <span class="ml20">
        版本: <tiny-select v-model="state.selectVersion" @change="versionChange" style="width:150px">
          <tiny-option v-for="item in state.versions" :key="item.value" :label="'opentiny/vue@' + item.value"
            :value="item.value">
          </tiny-option>
        </tiny-select>
      </span>
      <icon-share style="font-size: 16px;margin:0 20px; cursor: pointer;"  />
    </div>
  </div>
</template>

<script setup lang="ts">
import { reactive } from 'vue'
import { IconShare } from '@opentiny/vue-icon'
const iconShare = IconShare()

type typeStype={
  showCompileOutput: boolean
  showImportMap:boolean,
  layout:string,
  layoutOptions: string[],
  versions:string[],
  selectVersion:string
}
const state = reactive<typeStype>({
  // repl 属性
  showCompileOutput: true,
  showImportMap: true,
  layout: 'horizon',
  layoutOptions: [{ value: 'horizon', text: "水平" }, { value: 'vertical', text: "垂直" }],
  // 版本切换
  versions: [{ value: "3.8.0" }, { value: "3.8.1" }, { value: "3.8.2" }, { value: "3.8.3" }, { value: "3.8.4" }],
  selectVersion: "3.8.4"
})

const createImportMap = (version:string) => {
  return {
    imports: {
      "@opentiny/vue": `https://unpkg.com/@opentiny/vue@${version}/runtime/tiny-vue.mjs`,
      "@opentiny/vue-icon": `https://unpkg.com/@opentiny/vue@${version}/runtime/tiny-vue-icon.mjs`,
      "@opentiny/vue-locale": `https://unpkg.com/@opentiny/vue@${version}/runtime/tiny-vue-locale.mjs`,
      "@opentiny/vue-common": `https://unpkg.com/@opentiny/vue@${version}/runtime/tiny-vue-common.mjs`
    }
  }
};

function versionChange(version:string) {
  const importMap = createImportMap(version)
  store.setImportMap(importMap);
  state.previewOptions.headHTML = `<link rel="stylesheet" href="https://unpkg.com/@opentiny/vue-theme@${version}/index.css">`
}

</script>

<style scoped>

</style>