<template>
  <a @click="getOAuth">go</a>
</template>

<script>
import {defineComponent} from 'vue';

export default defineComponent({
    name: 'OAuthComponent',
    data() {
        const apikey = '85ee49b55309620d949e79300a1d03e1';
        const redirectUri = 'http://localhost:8080/';
        return {
            kakaoOAuhUri: `https://kauth.kakao.com/oauth/authorize?response_type=code&client_id=${apikey}&redirect_uri=${redirectUri}`
        }
    },
    methods: {
        getOAuth() {
            window.location.href = this.kakaoOAuhUri;
        },
    }
})
</script>

<style>

</style>