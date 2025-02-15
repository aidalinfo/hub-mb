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

  <Card class="border-transparent border-4 hover:border-primary transition">
    <CardHeader class="grid grid-cols-[minmax(0,1fr)_110px] items-start gap-4 space-y-0">
      <div class="space-y-1">
        <CardTitle class="flex items-center space-x-2">
            <slot name="title" />
        </CardTitle>
        <CardDescription>
            <slot name="description" />
        </CardDescription>
      </div>
      <div class="flex items-center space-x-1 rounded-md text-secondary-foreground justify-self-end">
        <slot name="icon" />
      </div>
    </CardHeader>
  </Card>
</a>
</template>