<script setup lang="ts">
import { Button } from '@/components/ui/button'
import { DropdownMenu, DropdownMenuContent, DropdownMenuItem, DropdownMenuLabel, DropdownMenuSeparator, DropdownMenuTrigger } from '@/components/ui/dropdown-menu'
import { Input } from '@/components/ui/input'
import { Sheet, SheetContent, SheetTrigger } from '@/components/ui/sheet'
import { CircleUser, Menu, Package2, Search, Github } from 'lucide-vue-next'
</script>

<template>
  <div class="flex min-h-screen w-full flex-col">
    <header class="sticky top-0 flex h-16 items-center gap-4 border-b bg-background px-4 md:px-6">
      <nav class="hidden flex-col gap-6 text-lg font-medium md:flex md:flex-row md:items-center md:gap-5 md:text-sm lg:gap-6">
        <a
          href="/"
          class="flex items-center gap-2 text-lg font-semibold md:text-base"
        >
          <Package2 class="h-6 w-6 text-black" />
        </a>
        <a
          href="/"
          class="text-muted-foreground transition-colors hover:text-primary"
        >
          Accueil
        </a>
        <a
          href="/modules/official"
          class="text-muted-foreground transition-colors hover:text-primary"
        >
          Officiel 
        </a>
        <a
          href="#"
          class="text-muted-foreground transition-colors hover:text-primary"
        >
          Communautaire
        </a>
      </nav>
      <Sheet>
        <SheetTrigger as-child>
          <Button
            variant="outline"
            size="icon"
            class="shrink-0 md:hidden"
          >
            <Menu class="h-5 w-5" />
            <span class="sr-only">Toggle navigation menu</span>
          </Button>
        </SheetTrigger>
        <SheetContent side="left">
          <nav class="grid gap-6 text-lg font-medium">
            <a
              href="/"
              class="flex items-center gap-2 text-lg font-semibold"
            >
              <Package2 class="h-6 w-6" />
            </a>
            <a
          href="/"
          class="text-muted-foreground transition-colors hover:text-primary"
        >
          Accueil
        </a>
        <a
          href="/modules/official"
          class="text-muted-foreground transition-colors hover:text-primary"
        >
          Officiel 
        </a>
        <a
          href="#"
          class="text-muted-foreground transition-colors hover:text-primary"
        >
          Communautaire
        </a>
          </nav>
        </SheetContent>
      </Sheet>
      <div class="flex w-full items-center gap-4 md:ml-auto md:gap-2 lg:gap-4">
        <form class="ml-auto flex-1 sm:flex-initial">
          <div class="relative">
            <!-- TODO mettre des links  -->
             <a href="https://github.com/aidalinfo/mini-backup" target="_blank">
            <Github class="h-6 w-6 rounded-full" />
          </a>
          </div>
        </form>
      </div>
    </header>
    <main class="flex min-h-[calc(100vh_-_theme(spacing.16))] flex-1 flex-col gap-4 bg-muted/50 p-4 md:gap-8 md:p-10">
      <slot />
    </main>
  </div>
</template>