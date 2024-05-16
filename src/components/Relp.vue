<template>
    <Repl  
        :store="store" 
        :editor="CodeMirror"
        :show-compile-output="state.showCompileOutput"
        :show-import-map="state.showImportMap" 
        :previewOptions="state.previewOptions" 
        :clear-console="false"
        :layout="state.layout">
    </Repl>
</template>

<script setup>
import { Repl,useStore} from '@vue/repl'
import CodeMirror from '@vue/repl/codemirror-editor'
import { defineProps, reactive,ref } from "vue";
import '@vue/repl/style.css'
// repl组件需要store管理状态
const sfcOptions = ref({})
 useStore({ sfcOptions })

const state = reactive({
    layout: 'horizontal',
    // previewOptions: { headHTML: '' },
    previewOptions: { headHTML: '' },
})
</script>

<style lang="scss" scoped></style>