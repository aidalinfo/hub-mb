<script setup lang="ts">
import Container from '../layout/Container.vue';
import CardModuleInternal from './CardModuleInternal.vue';
import CardModuleCommunity from './CardModuleCommunity.vue';
import { Input } from '@/components/ui/input'
import { Search } from 'lucide-vue-next'
</script>
<template>
    <Container >
        <div class="text-center max-w-3xl mx-auto mb-12">
            <h1 class="text-4xl font-bold text-primary">Minibackup Hub</h1>
                <p class="text-lg text-gray-500 mt-2">
                    Gérez vos sauvegardes en toute simplicité, créez, utilisez et partagez des modules adaptées à vos infrastructures.                </p>
            <div class="mt-6 flex justify-center space-x-4">
                <div class="relative w-full max-w-sm items-center border-2 border-primary rounded-md bg:hover">
                    <Input id="search" type="text" placeholder="Rechercher un module" class="w-full rounded-md border-0 py-2 pl-10 pr-4 text-sm placeholder:text-muted-foreground focus:outline-none focus:ring-0" />
                    <span class="absolute start-0 inset-y-0 flex items-center justify-center px-2">
                    <Search class="size-6 text-muted-foreground" />
                    </span>
                </div>
            </div>
        </div>

        <CardModuleInternal class="mb-4" />
        <CardModuleCommunity />
    </Container>
</template>