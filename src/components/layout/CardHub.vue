<script setup lang="ts">
import {
  Card,
  CardContent,
  CardDescription,
  CardHeader,
  CardTitle,
} from '@/components/ui/card'

defineProps({
  path: {
    type: String,
    required: true,
  }
});
</script>

<template>
  <a :href="path" class="block">
    <Card class="border border-transparent hover:border-primary transition bg-background p-4 shadow-lg">
      <div class="flex items-center gap-4">
        
        <!-- IMAGE À GAUCHE -->
        <div class="w-14 h-14 flex-shrink-0 rounded-lg overflow-hidden" v-if="$slots.image">
          <slot name="image" />
        </div>

        <!-- CONTENU PRINCIPAL -->
        <div class="flex flex-col flex-1 space-y-1">
          
          <!-- Titre + Badge sur la même ligne -->
          <div class="flex items-center gap-2">
            <CardTitle class="text-lg font-semibold capitalize">
              <slot name="title" />
            </CardTitle>
          </div>

          <!-- Description -->
          <CardDescription class="text-sm">
            <slot name="description" />
          </CardDescription>

        </div>

        <!-- ICÔNE À DROITE -->
        <div class="flex items-center justify-center text-secondary-foreground">
          <slot name="icon" />
        </div>

      </div>

      <!-- Contenu en bas -->
      <CardContent class="mt-3">
        <slot name="content" />
      </CardContent>
      
    </Card>
  </a>
</template>
