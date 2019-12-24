<template>
    <div class="header-container">
        <div class="header-title">
            <span>{{title}}</span>
        </div>
        <div class="right-container">
            <div class="search">
                <v-icon>mdi-magnify</v-icon>
            </div>
            <div class="user-wrapper">
                <v-img
                    src="../assets/images/40c8d09e0514c9e78934978246b414fe251e3983.png"
                    class="logo-img"
                    max-width="100%"
                ></v-img>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "headerTop",
        data() {
            return {
                title: 'Invite',
            }
        }
    }
</script>

<style scoped>
    .header-container {
        padding: 40px 50px 40px 20px;
        display: flex;
        justify-content: space-between;
        width: 100%;
        align-items: center;
    }
    .header-title {
        display: flex;
        align-items: center;
    }
    .header-title span {
        font-size: 23px;
        font-weight: 600;
    }
    .search {
        padding: 15px;
        background-color: #f5f5f5;
        border-radius: 50%;
        cursor: pointer;
        margin-right: 20px;
    }
    .search i {
        font-size: 21px;
        color: #000;
    }
    .user-wrapper {
        overflow: hidden;
        border-radius: 50%;
        border: 3px solid #07a766;
        width: 50px;
        height: 50px;
    }
    .right-container {
        display: flex;
    }
</style>
