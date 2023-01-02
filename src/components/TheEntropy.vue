<script setup>
import { ref } from 'vue'

defineProps(['title'])

const entropyGroup = ref([
    {
        col_xs: 12,
        col_sm: 12,
        col_md: 6,
        col_lg: 8,
        icon: "error",
        title: "Très faible",
        subtitle: "Entropie < 28 bits"
    },
    {
        col_xs: 12,
        col_sm: 12,
        col_md: 6,
        col_lg: 8,
        icon: "warning",
        title: "Faible",
        subtitle: "Entropie <= 35 bits"
    },
    {
        col_xs: 12,
        col_sm: 12,
        col_md: 6,
        col_lg: 8,
        icon: "info",
        title: "Raisonnable",
        subtitle: "Entropie <= 59 bits"
    },
    {
        col_xs: 12,
        col_sm: 12,
        col_md: 12,
        col_lg: 12,
        icon: "success",
        title: "Robuste",
        subtitle: "Entropie <= 127 bits"
    },
    {
        col_xs: 12,
        col_sm: 12,
        col_md: 12,
        col_lg: 12,
        icon: "success",
        title: "Très robuste, voir inutile",
        subtitle: "Entropie >= 128 bits"
    },
])
</script>
<template>
    <el-card>
        <el-row>
            <el-col v-show="title">
                <h3>Entropie: {{ title[0] }} bits, {{ title[1] }}</h3>
            </el-col>
        </el-row>
        <el-row justify="center">
            <div v-for="entropy in entropyGroup">
                <div :xs="entropy.col_xs" :sm="entropy.col_sm" :md="entropy.col_md" :lg="entropy.col_lg">
                    <el-result :icon="entropy.icon" :title="entropy.title" :sub-title="entropy.subtitle">
                    </el-result>
                </div>
            </div>
        </el-row>
    </el-card>
</template>
