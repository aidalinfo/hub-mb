<script setup lang="ts">
import CardHub from '@/components/layout/CardHub.vue';
import { StepForward, Package } from 'lucide-vue-next';
</script>

<template>
    <CardHub path="/modules/official">
        <template #title>
            <Package class="mr-2" />
            Module officiel
        </template>
        <template #description>
            Module de sauvegarde officiel créé par les mainteneurs de MiniBackup
        </template>
        <template #icon>
            <step-forward  />
        </template>
    </CardHub>
</template>