<script setup>
import { Card, CardContent, CardHeader, CardTitle, CardDescription } from '@/components/ui/card'
import Container from '../layout/Container.vue';
import CardHub from '@/components/layout/CardHub.vue';
import { StepForward, Search } from 'lucide-vue-next';
import { Badge } from '@/components/ui/badge'
import { Input } from '../ui/input';

// Importer uniquement les modules "official"
const modules = (await import('@/modules-minibackup/.index.json')).official;
</script>

<template>
  <Container>
    <div class="text-left max-w-3xl mx-auto mb-12">
      <h2 class="text-4xl font-bold text-primary">Modules officiels</h2>
      <p class="text-lg text-gray-500 mt-2">
        Retrouvez ici les modules officiels disponibles pour MiniBackup.
      </p>
      <div class="mt-6 flex justify-left space-x-4">
        <!-- <div class="relative w-full max-w-sm items-left border-2 border-primary rounded-md bg:hover">
                    <Input id="search" type="text" placeholder="Rechercher un module" class="w-full rounded-md border-0 py-2 pl-10 pr-4 text-sm placeholder:text-muted-foreground focus:outline-none focus:ring-0" />
                    <span class="absolute start-0 inset-y-0 flex items-center justify-center px-2">
                    <Search class="size-6 text-muted-foreground" />
                    </span>
                </div> -->
      </div>
    </div>

    <div v-if="modules && Object.keys(modules).length">
      <div v-for="(module, moduleName) in modules" :key="moduleName" class="mb-4">
        <CardHub :path="`/modules/official/${moduleName}`">
          <template #image>
            <img src="/default_module.png" alt="Module Image">
          </template>
          <template #title>
            <div class="flex items-center gap-2">
              <h3 class="text-lg font-semibold capitalize">{{ moduleName }}</h3>
              <Badge class="text-xs">
                Official
              </Badge>
            </div>
          </template>

          <template #description>
            <p class="text-gray-500 italic flex items-center">
              version : {{ module.version }} by
              <a :href="`https://github.com/${module.metadata.author}`" target="_blank"
                class="text-primary font-medium hover:underline ml-1">
                @{{ module.metadata.author }}
              </a>
            </p>

          </template>
          <template #content>
            <p>
              {{ module.metadata.description }}
            </p>
          </template>
        </CardHub>
      </div>

    </div>
  </Container>


  <!-- <Card class="w-full p-4">
    <CardHeader>
      <CardTitle>Modules Officiels</CardTitle>
      <CardDescription>Liste des modules officiels disponibles</CardDescription>
    </CardHeader>
    <CardContent>
      <div v-if="modules && Object.keys(modules).length">
        <ul class="mt-2 space-y-2">
          <li v-for="(module, moduleName) in modules" :key="moduleName" class="p-3 border rounded-lg shadow-sm">
            <div class="flex justify-between">
              <div>
                <strong class="text-base font-medium">{{ moduleName }}</strong>
                <span class="ml-2 text-sm text-gray-500">v{{ module.version }} ({{ module.type }})</span>
              </div>
              <a :href="module.path" target="_blank" class="text-blue-500 hover:underline text-sm">
                Voir détails
              </a>
            </div>
          </li>
        </ul>
      </div>
      <p v-else class="text-gray-500 italic">Aucun module officiel disponible.</p>
    </CardContent>
  </Card> -->
</template>
