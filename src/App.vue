<template>
    <o-auth-component/>
    <o-auth-result-component/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import OAuthComponent from './components/OAuthComponent.vue';
import OAuthResultComponent from './components/OAuthResultComponent.vue';

export default defineComponent({
  name: 'App',
  components: {
    OAuthComponent,
    OAuthResultComponent
  }
});
</script>

<style>
</style>
