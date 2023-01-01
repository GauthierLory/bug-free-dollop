<script setup>
import { ref } from 'vue'

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
        title: "Fort",
        subtitle: "Entropie <= 127 bits"
    },
    {
        col_xs: 12,
        col_sm: 12,
        col_md: 12,
        col_lg: 12,
        icon: "success",
        title: "Très fort",
        subtitle: "Entropie >= 128 bits"
    },
])
</script>
<template>
    <el-card>
        <el-row justify="center">
            <div v-for="entropy in entropyGroup">
                <e-col :xs="entropy.col_xs" :sm="entropy.col_sm" :md="entropy.col_md" :lg="entropy.col_lg">
                    <el-result :icon="entropy.icon" :title="entropy.title" :sub-title="entropy.subtitle">
                    </el-result>
                </e-col>
            </div>
        </el-row>
    </el-card>
</template>
