<script setup>
import { ref } from 'vue'

const includeUppercase = ref(false)
const includeSymbols = ref(false)
const includeNumbers = ref(false)
const numbersOfCharacters = ref(5)

const password = ref('')
const entropy = ref('')
const message = ref('')
const max = ref(80)
const min = ref(1)

const UPPERCASE_CHAR_CODES = arrayFromLowToHigh(65, 90)
const LOWERCASE_CHAR_CODES = arrayFromLowToHigh(97, 122)
const NUMBER_CHAR_CODES = arrayFromLowToHigh(48, 57)
const SYMBOL_CHAR_CODES = arrayFromLowToHigh(33, 47).concat(
    arrayFromLowToHigh(58, 64)
).concat(
    arrayFromLowToHigh(91, 96)
).concat(
    arrayFromLowToHigh(123, 126)
)

function form(e) {
    password.value = generatePassword(numbersOfCharacters.value, includeUppercase.value, includeNumbers.value, includeSymbols.value)
    e.preventDefault();
    return password.value
}

function generatePassword(characterAmount, includeUppercase, includeNumbers, includeSymbols) {

    let charCodes = LOWERCASE_CHAR_CODES
    let possibilityCharacter = 26
    if (includeUppercase) {
        charCodes = charCodes.concat(UPPERCASE_CHAR_CODES)
        possibilityCharacter += 26;
    }
    if (includeSymbols) {
        charCodes = charCodes.concat(SYMBOL_CHAR_CODES)
        possibilityCharacter += 33;
    }
    if (includeNumbers) {
        charCodes = charCodes.concat(NUMBER_CHAR_CODES)
        possibilityCharacter += 10;
    }

    generateEntropy(possibilityCharacter, characterAmount)

    const passwords = []
    for (let index = 0; index < 10; index++) {
        const passwordCharacters = []
        for (let i = 0; i < characterAmount; i++) {
            const characterCode = charCodes[Math.floor(Math.random() * charCodes.length)]
            passwordCharacters.push(String.fromCharCode(characterCode))
        }
        passwords.push(passwordCharacters.join(''))
    }
    return passwords
}

function generateEntropy(possibilityCharacter, characterAmount) {
    const possibilityNum = Math.pow(possibilityCharacter, characterAmount)
    const pEntropy = (Math.log(possibilityNum) / Math.LN2).toFixed(2);

    if (pEntropy < 28) {
        message.value = "mot de passe très faible"
    } else if (pEntropy <= 35) {
        message.value = "mot de passe faible"
    } else if (pEntropy <= 59) {
        message.value = " mot de passe raisonnable"
    } else if (pEntropy <= 127) {
        message.value = " mot de passe robuste"
    } else if (pEntropy >= 128) {
        message.value = "mot de passe très robuste"
    }
    entropy.value = pEntropy
    return pEntropy;
}

function arrayFromLowToHigh(low, high) {
    const array = []
    for (let i = low; i <= high; i++) {
        array.push(i)
    }
    return array
}

function clickToCopy(passwd) {
    navigator.clipboard.writeText(passwd);
    alert("Le mot de passe a été copié.");
}
</script>
<template>
    <el-card shadow="hover">
        <template #header>
            <h1>Générateur de mot de passe</h1>
        </template>
        <el-row>
            <el-col>
                <el-form id="passwordGeneratorForm" @submit.prevent>
                    <span>Nombre de caractères</span>
                    <el-slider :max="max" :min="min" v-model="numbersOfCharacters" />
                    <el-checkbox v-model="includeUppercase" label="Avec majuscules" size="large" />
                    <el-checkbox v-model="includeNumbers" label="Avec les nombres" size="large" />
                    <el-checkbox v-model="includeSymbols" label="Avec les symbols" size="large" />
                </el-form>
            </el-col>
        </el-row>
        <el-row>
            <el-col>
                <el-button type="primary" @click="form">Générer les mots de passe</el-button>
            </el-col>
        </el-row>
        <el-row>
            <el-col>
                <h3 v-show="entropy">Entropie: {{ entropy }} bits, {{ message }}</h3>
                <el-tag class="tag" @click="clickToCopy(passwd)" v-for="passwd in password" :key="passwd">
                    {{ passwd }}
                </el-tag>
            </el-col>
        </el-row>
    </el-card>
</template>

<style>
.tag {
    margin-left: 4px;
    margin-bottom: 4px;
}
</style>