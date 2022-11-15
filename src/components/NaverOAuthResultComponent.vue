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
            apikey: 'AB20zOvKO_vZxeJIThxA',
            secretKey: 'o84LjsGvN7'
        }
    },
    async created() {
        await this.getToken();
        await this.getProfile();
    },
    methods: {
        async getToken() {
            //C.F : 
            const uri = window.location.search.substring(1);
            const params = new URLSearchParams(uri); 
            const tokenRes = await axios.get(`http://localhost:3000?code=${params.get('code')}`);
            this.token = tokenRes.data.access_token;
        },
        async getProfile() {
            const profile = await axios.get(`http://localhost:3000/me`, {
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