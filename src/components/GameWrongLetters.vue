<script setup lang="ts">
interface Props {
    wrongLetters: string[]
}

defineProps<Props>()
</script>

<template>
    <div 
        class="wrong-letters-container"
        v-if="wrongLetters.length" 
    >
        <div class="wrong-letters">
            <p>Ошибки</p>
            <span v-for="(letter, index) in wrongLetters" key="letter">
                {{ index === wrongLetters.length - 1 ? letter : `${letter}, ` }}
            </span>
        </div>
    </div>  
</template>