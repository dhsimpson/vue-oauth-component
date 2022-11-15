<template>
  <a @click="getOAuth">naver</a>
</template>

<script>
import {defineComponent} from 'vue';

export default defineComponent({
    name: 'OAuthComponent',
    data() {
    // apiURL += "&state=" + state;
        const apikey = 'AB20zOvKO_vZxeJIThxA';
        const redirectUri = 'http://localhost:8080/';
        return {
            naverOAuhUri: `https://nid.naver.com/oauth2.0/authorize?response_type=code&client_id=${apikey}&redirect_uri=${redirectUri}`
        }
    },
    methods: {
        getOAuth() {
            window.location.href = this.naverOAuhUri;
        },
    }
})
</script>

<style>

</style>