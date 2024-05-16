<script setup>
import { reactive } from 'vue';
import Header from './components/Header.vue';
import Relp from './components/Relp.vue';
</script>

<template>

<div>
  <Header></Header>
  <Relp/>
 
</div>

</template>

<style>
 * {  box-sizing: border-box;}
.header {
  height: 36px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding-bottom: 6px;
  border-bottom: solid 1px #e1e1e1;
}
.vue-repl {  height: calc(100vh - 36px - 16px) !important;}
.header > div {  vertical-align: middle;}
.title {  font-size: 20px;}
.ml20 {  margin-left: 20px;}
</style>