<template>
    <table v-if="table">
        <slot name="prepend"></slot>
        <tbody>
            <slot></slot>
        </tbody>
        <slot name="append"></slot>
    </table>
    <div v-else>
        <slot name="prepend"></slot>
        <slot></slot>
        <slot name="append"></slot>
    </div>
</template>
  
<script lang="ts" setup>

// TODO 由于和树结合可能不需要table
import { defineProps, toRefs } from "vue"
const props = defineProps({
    table: Boolean
})
const { table } = toRefs(props)

</script>