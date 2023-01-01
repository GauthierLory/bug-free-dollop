<script setup>
import TheHelloWorld from './components/TheHelloWorld.vue';
import TheFormPassword from './components/TheFormPassword.vue';
import TheEntropy from './components/TheEntropy.vue';
import TheFaq from './components/TheFaq.vue';

</script>
<template>
  <main>
    <TheHelloWorld class="content" />
    <TheFormPassword class="content" />
    <TheEntropy class="content" />
    <TheFaq class="content" />
  </main>
</template>
<style>
body {
  background: rgb(21, 186, 221);
  background: linear-gradient(90deg, rgba(21, 186, 221, 1) 0%, rgba(0, 36, 130, 1) 100%);
  font-family: 'Helvetica Neue'
}

.content {
  margin-top: 20px;
}

main {
  display: block;
  margin-left: auto;
  margin-right: auto;
}

@media (min-width: 768px) {
  main {
    width: 70%;
  }
}

@media (min-width: 1024px) {
  main {
    width: 60%;
  }
}

@media (min-width: 1820px) {
  main {
    width: 60%;
  }
}

@media (min-width: 2200px) {
  main {
    width: 50%;
  }
}

.el-row {
  margin-bottom: 20px;
}

.el-row:last-child {
  margin-bottom: 0;
}

.el-col {
  border-radius: 4px;
}

.grid-content {
  border-radius: 4px;
  min-height: 36px;
}
</style>
