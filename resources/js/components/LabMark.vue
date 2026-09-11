<script setup lang="ts">
import AppLogoIcon from '@/components/AppLogoIcon.vue';

defineOptions({
    inheritAttrs: false,
});
</script>

<template>
    <AppLogoIcon v-bind="$attrs" />
</template>
