<template>
    <div>
    <div id="card-content">
        <div id="picture-profile">
            <img :src="infoProfile.avatar_url" :alt="infoProfile.login" width="110" height="110"/>
        </div>
        <div id="description-profile">
            <h2>{{ infoProfile.login }}</h2>
            <small id="bio-profile">{{ infoProfile.bio }}</small>
        </div>
        <div id="networking-profile">
            <span>Seguindo: {{ infoProfile.following }}</span>
            <span>Seguidores: {{ infoProfile.followers }}</span>
        </div>
        <div id="date-profile">
            <small>Desde: {{infoProfile.created_at }}</small>
        </div>
    </div>
    <div id="go-profile">
        <button id="goBtn-profile" @click="redirectToProfile(infoProfile.html_url)">Vizualizar Perfil</button>
    </div>
</div>
</template>

<script>
export default {
    props: {
        infoProfile: Object
    },
    methods: {
        redirectToProfile(linkProfile){
            window.location.href = linkProfile
        },
    },
}
</script>

<style scoped src="../styles/CardProfile.css"></style>