<script lang="ts" setup>
import { ref } from 'vue';

const props = defineProps({
    placeHolder: { type: String, required: true },
    type: { type: String, required: true },
    errorMessage: { type: String, required: true }
})

const emits = defineEmits(['input'])

const value = ref('');

</script>

<template>
    <div>
        <img v-if="errorMessage" src="../assets/images/icon-error.svg" alt="error">
        <input :class="props.errorMessage ? 'error' : ''" :type="type" :placeholder="props.placeHolder" v-model="value" @change="emits('input', value)">
        <small v-if="errorMessage">{{ errorMessage }}</small>
    </div>
</template>

<style scoped>
div {
    position: relative;
    margin-block-end: 1rem;
}
    img {
        position: absolute;
        right: 2rem;
        transform: translate(0, 60%);
    }
    input {
        width: calc(100% - 6rem);
        padding: 1rem 4rem 1rem 2rem;
        border-radius: 0.5rem;
        border-width: thin;
        color: hsl(249, 10%, 26%) ;
        font-family: Poppins, sans-serif;
        margin-block-end: 0.5rem;
    }
        input:focus {
            outline-color: hsl(248, 32%, 49%);
        }

        input::placeholder {
            font-weight: 700;
        }

        small {
            display: block;
            font-size: 0.75rem;
            text-align: right;
            color: hsl(0, 100%, 74%);
        }

        .error {
            border-color: hsl(0, 100%, 74%) ;
        }

</style>