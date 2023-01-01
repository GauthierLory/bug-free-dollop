<script setup>
const content = `Cette application de génération de mots de passe vous offre la possibilité de créer des mots de passe forts et
    sécurisés pour protéger vos comptes en ligne. Vous pouvez choisir la longueur et la complexité de votre mot de passe, ainsi que les caractères à inclure, 
    ce qui vous permet de créer des mots de passe ayant une <b>entropie</b> élevée, c'est-à-dire une mesure de leur robustesse et de leur complexité.`
    // En utilisant notre application, vous pouvez être sûr que vous prenez des mesures pour renforcer la sécurité de vos comptes en ligne.
</script>
<template>
  <el-card>
    <p v-html="content" />
  </el-card>
</template>

<style scoped>
p {
  font-size: 16px;
  margin-top: 50px;
  margin-bottom: 50px;
  text-align: justify
}
</style>
