<template>
    <kakao-o-auth-component/>
    <kakao-o-auth-result-component/>
    <naver-o-auth-component/>
    <naver-o-auth-result-component/>
    <google-o-auth-component/>
    <google-o-auth-result-component/>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import GoogleOAuthComponent from './components/GoogleOAuthComponent.vue';
import GoogleOAuthResultComponent from './components/GoogleOAuthResultComponent.vue';
import KakaoOAuthComponent from './components/KakaoOAuthComponent.vue';
import KakaoOAuthResultComponent from './components/KakaoOAuthResultComponent.vue';
import NaverOAuthComponent from './components/NaverOAuthComponent.vue';
import NaverOAuthResultComponent from './components/NaverOAuthResultComponent.vue';

export default defineComponent({
  name: 'App',
  components: {
      KakaoOAuthComponent,
      KakaoOAuthResultComponent,
      NaverOAuthComponent,
      NaverOAuthResultComponent,
      GoogleOAuthComponent,
      GoogleOAuthResultComponent,
  }
});
</script>

<style>
</style>
    