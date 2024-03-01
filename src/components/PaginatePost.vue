<script setup>
import { computed } from 'vue';


// const emit = defineEmits(['next', 'previous'])

const props = defineProps({
    inicio: Number,
    fin: Number,
    top: Number
});

const prev = computed(() => {
    return (props.inicio <= 0)
})
const nxt = computed(() => {
    return (props.fin >= props.top)
})

</script>

<template>
    <div class="btn-group" role="group" aria-label="Basic example">
        <button @click="$emit('previous')" type="button" class="btn btn-outline-primary" :disabled='prev'>Previous
            {{ props.inicio }} - {{ prev }}</button>
        <button @click="$emit('next')" type="button" class="btn btn-outline-primary" :disabled='nxt'>Next
            {{ props.fin }}- {{ nxt }}</button>
    </div>
</template>

<style></style>