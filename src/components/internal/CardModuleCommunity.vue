<script setup lang="ts">
import CardHub from '@/components/layout/CardHub.vue';
import { StepForward, Puzzle } from 'lucide-vue-next';
</script>

<template>
    <CardHub path="/modules/community">
        <template #title>
            <Puzzle class="mr-2" />
            Module communautaire
        </template>
        <template #description>
            Module de sauvegarde communautaire créé par la communauté
        </template>
        <template #icon>
            <step-forward  />
        </template>
    </CardHub>
</template>