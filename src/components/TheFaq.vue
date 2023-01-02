<template>
    <el-card>
        <el-collapse accordion>
            <el-collapse-item v-for="content in contents">
                <template #title>
                    <h2>{{ content.title }}</h2>
                </template>
                <p v-html="content.content" />
            </el-collapse-item>
        </el-collapse>
    </el-card>
</template>
  
<script setup>
const contents = [
    {
        title: 'Calculer la force du mot de passe ?',
        content: `La force du mot de passe est déterminée à l'aide de ce tableau :
            <ul>
                <li>moins de 28 bits = très faible ; peut empêcher les membres de la famille d'entrer.</li>
                <li>28 - 35 bits = Faible ; devrait empêcher la plupart des gens d'entrer, souvent bon pour les mots
                    de passe de connexion au bureau.</li>
                <li>36 - 59 bits = Raisonnable ; mots de passe assez sûrs pour les mots de passe de réseau et
                    d'entreprise</li>
                <li>60 - 127 bits = Fort ; peut être bon pour protéger des informations financières.</li>
                <li>128+ bits = Très fort ; souvent excessif.</li>
            </ul>
            Si un mot de passe de 40 à 50 bits d'entropie peut être semi-sûr aujourd'hui, ce n'est qu'une question
            de temps avant que les
            GPU
            deviennent plus puissants et que le craquage de mots de passe prenne moins de temps !`
    },
    {
        title: ` Calculer l'entropie d'un mot de passe ?`,
        content: ` Nous calculons l'entropie d'un mot de passe en examinant d'abord le pool de caractères dont il est
                composé. Par exemple, le mot de passe a une possibilité de 26 caractères de l'alphabet francais/anglais.
                En remplaçant le mot de passe par "Password", vous augmenteriez votre pool à 52, 26 caractères minuscules et 26 caractères majuscules
                Exemple de type de caractères:
            <ul>
                <li>Minuscules 26</li>
                <li>Minuscules et majuscules 52</li>
                <li>Alphanumérique 36</li>
                <li>Alphanumérique et majuscule 62</li>
                <li>Caractères ASCII courants 30</li>
                <li>Liste de mots du Diceware 7 776</li>
                <li>Mots du dictionnaire Francais 150 000</li>
            </ul>`
    },
]
</script>
<style scoped>
p {
    font-size: 16px;
    text-align: justify
}
</style>