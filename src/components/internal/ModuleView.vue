<script setup lang="ts">
import { defineProps, onMounted, ref } from 'vue';
import LargeContainer from '../layout/LargeContainer.vue';
import Badge from '../ui/badge/Badge.vue';
import { SquareTerminal, Ellipsis, ClipboardCopy, FileCode, ArrowLeftToLine } from 'lucide-vue-next';
import { marked } from 'marked';
import Toaster from '@/components/ui/toast/Toaster.vue'
import { Separator } from '@/components/ui/separator'
import {
    Card,
    CardContent,
    CardHeader,
} from '@/components/ui/card'
import { useToast } from '@/components/ui/toast/use-toast'
const { toast } = useToast()
const markdownFiles = import.meta.glob('@/modules-minibackup/modules/**/**/*.md', { query: '?raw', import: 'default' });
const markdownContent = ref();
marked.use({
  async: true,
  pedantic: false,
  gfm: true,
});
const props = defineProps({
    module: {
        type: Object,
        required: true,
    },
    name: {
        type: String,
        required: true,
    },
});

const copyToClipboard = () => {
    navigator.clipboard.writeText('minibackup module install ' + props.name).then(() => {
        toast({
            title: '🎉 Commande copiée dans le presse-papier 🎉',
            description: 'Vous pouvez la coller dans votre terminal',
            duration: 3000,
        })
    })
}


const loadMarkdown = async () => {
    try {
        const markdownFileKey = Object.keys(markdownFiles).find(key => key.endsWith(props.module.path));
        if (markdownFileKey) {
            const rawContent = await markdownFiles[markdownFileKey]() as string; // ✅ Charge le contenu brut
            markdownContent.value = await marked.parse(rawContent);
        } else {
            markdownContent.value = '*Erreur : Fichier Markdown introuvable*';
        }
    } catch (error) {
        console.error("Erreur lors du chargement du Markdown :", error);
        markdownContent.value = '*Erreur lors du chargement de la description*';
    }
};


onMounted(async() => {
    await loadMarkdown();
});
const goBack = () => {
  window.history.back();
};

</script>
<template>
    <Toaster />
      <LargeContainer>
        <div class="flex items-center mb-4" @click="goBack">
            <ArrowLeftToLine  class="mr-2" />
            <span>Retour à la liste des modules</span>
        </div>

        <div class="text-left w-full mb-12 flex items-center space-x-4">
            <img class="h-16 w-16 rounded-full flex-shrink-0" src="/default_module.png" alt="Module Image">
            <div>
                <h2 class="text-4xl font-bold text-primary">{{ props.name }}</h2>
                <p class="text-lg text-gray-500 mt-1">
                    version : {{ props.module.version }} by
                    <span class="text-primary font-medium">{{ props.module.metadata.author }}</span>
                </p>
                <Badge class="text-xs mt-2">Official</Badge>
                <p class="mt-2">{{ props.module.metadata.description }}</p>
            </div>
        </div>
        <div>
            <div class="flex items-center space-x-2">
                <SquareTerminal class="h-6 w-6" />
                <span>Installation</span>
            </div>
            <Separator class="bg-primary h-1 rounded-full w-full mt-2 mb-4" />
            <Card class="mb-12">
                <CardHeader>
                    <Ellipsis />
                </CardHeader>
                <CardContent class="flex items-center justify-between">
                    <p>minibackup module install {{ props.name }}</p>
                    <div class="flex flex-col items-end">
                        <ClipboardCopy class="cursor-pointer hover:text-primary" @click="copyToClipboard" />
                    </div>
                </CardContent>
            </Card>
            <div class="flex items-center space-x-2 mb-4">
                <FileCode class="h-6 w-6" />
                <span>Documentation</span>
            </div>
            <Separator class="bg-primary h-1 rounded-full w-full mt-2 mb-4" />
            <Card v-if="markdownContent">
                <CardContent>
                <div class="prose mt-4" v-html="markdownContent"></div>
            </CardContent>
            </Card>
        </div>
    </LargeContainer>
</template>