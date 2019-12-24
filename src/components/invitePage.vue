<template>
    <div class="invite-container">
        <div class="left-container" :class="{'left-container-close': !openMenuStatus}">
            <leftSidebar @clicked="clickedSmallMenu"/>
        </div>
        <div class="right-container" :class="{'right-container-close': !openMenuStatus}">
            <headerPage />
            <inviteFriendsContent />
        </div>
    </div>
</template>

<script>
    import leftSidebar from '../layout/leftSidebar.vue';
    import headerPage from '../layout/headerTop.vue';
    import inviteFriendsContent from '../layout/inviteFriendsContent.vue';

    export default {
        name: "invitePage",
        data() {
            return {
                openMenuStatus: true
            }
        },
        components: {
            leftSidebar,
            headerPage,
            inviteFriendsContent
        },
        methods: {
            clickedSmallMenu (value) {
                this.openMenuStatus = value
            }
        }
    }
</script>

<style scoped>
    .invite-container {
        max-width: 1400px;
        width: 100%;
        margin: 0 auto;
        display: flex;
    }

    .left-container {
        width: 27%;
        transition: 0.4s;
    }

    .right-container {
        transition: 0.4s;
        width: 73%;
    }

    .left-container-close {
        width: auto;
    }

    .right-container-close {
        width: 100%;
    }

</style>
