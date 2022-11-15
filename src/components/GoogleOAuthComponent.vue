<template>
  <a @click="getOAuth">google</a>
</template>

<script>
import {defineComponent} from 'vue';

export default defineComponent({
    name: 'OAuthComponent',
    data() {
        const apikey = '942627775998-3dvhsoq9grhajkaavncp4gtsjh4ofprk.apps.googleusercontent.com';
        const redirectUri = 'http://localhost:8080/';
        return {
            googleOAuthUri: `https://accounts.google.com/o/oauth2/v2/auth?client_id=${apikey}&redirect_uri=${redirectUri}&response_type=token&scope=https://www.googleapis.com/auth/drive.metadata.readonly&include_granted_scopes=true&state=pass-through value`
        }
    },
    methods: {
        getOAuth() {
            window.location.href = this.googleOAuthUri;
        },
    }
})
</script>

<style>

</style>