<template>
    <p>{{profile}}</p>
</template>

<script>
import {defineComponent} from 'vue';
import axios from 'axios';

export default defineComponent({
    data() {
        return {
            profile: {},
            apikey: '85ee49b55309620d949e79300a1d03e1',
            redirectUri: 'http://localhost:8080/',
        }
    },
    async created() {
        await this.getToken();
        await this.getProfile();
    },
    methods: {
        async getToken() {
            const uri = window.location.search.substring(1);
            const params = new URLSearchParams(uri); 
            const res = await axios.get(`https://kauth.kakao.com/oauth/token?client_id=${this.apikey}&code=${params.get('code')}&redirect_uri=${this.redirectUri}&grant_type=authorization_code`, {
                headers: {
                    'Content-type': 'application/x-www-form-urlencoded;charset=utf-8'
                }
            });
            console.log(res.data.access_token)
            this.token = res.data.access_token
        },
        async getProfile() {
            const profile = await axios.get('https://kapi.kakao.com/v1/api/talk/profile', {
                headers: {
                    Authorization: `Bearer ${this.token}`
                }
            });
            console.log(profile)
            this.profile = profile;
        }
    }
})
</script>

<style>

</style>