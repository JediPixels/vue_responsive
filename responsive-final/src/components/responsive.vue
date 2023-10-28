<script setup lang="ts">
import { useMonitorSize } from '../composables/monitor-size';
import Mobile from './mobile.vue';
import Web from './web.vue';

const sizes = useMonitorSize();
</script>

<template>
    <h2>{{ sizes.browserWidth }} pixels: Browser </h2>
    <h2>{{ sizes.deviceWidth }} pixels: Device</h2>
  
    <Mobile v-if="sizes.isMobile.value" />
    <Web v-else />
</template>