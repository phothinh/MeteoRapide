<template>
    <div>
      <input v-model="phrase" type="text" placeholder="Entrez une phrase">
      <button @click="lirePhrase">Lire la phrase</button>
    </div>
</template>

<script lang="ts">
    export default {
        data() {
            return {
                phrase: '' as string|undefined,
            };
        },
        methods: {
            lirePhrase() {
                if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(this.phrase);
                window.speechSynthesis.speak(utterance);
                } else {
                console.log("L'API Speech Synthesis n'est pas prise en charge par ce navigateur.");
                }
            },
        },
    }
</script>