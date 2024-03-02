<script setup>
import { computed } from 'vue';


// const emit = defineEmits(['next', 'previous'])

const props = defineProps({
    inicio: Number,
    fin: Number,
    top: Number
});

</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button @click="$emit('previous')" type="button" class="btn btn-outline-primary"
            :disabled='(props.inicio <= 0)'>Previous</button>
        <button @click="$emit('next')" type="button" class="btn btn-outline-primary"
            :disabled='(props.fin >= props.top)'>Next</button>
    </div>
</template>

<style></style>