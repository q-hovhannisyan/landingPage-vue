<template>
    <div class="sidebar-container">
        <div class="sidebar-left-content">
            <div class="cubo-user cubo-item-1">
                <span>K</span>
                <div class="user-online-status" style="display: none"></div>
            </div>
            <div class="cubo-user user-active cubo-item-2">
                <span>al+</span>
                <div class="user-online-status" style="display: none"></div>
            </div>
            <div class="cubo-user cubo-item-3">
                <span>MD</span>
                <div class="user-online-status"></div>
            </div>
            <div class="cubo-user plus-item">
                <span>+</span>
            </div>
        </div>
        <div class="sidebar-right-content">
            <div class="menu-btn" @click="openLeftMenu" :class="{'menu-btn-go-to-right': !openMenuStatus}">
                <v-img
                        src="../assets/images/menu-btn-1.png"
                        class="menu-btn-img"
                        max-width="16"
                ></v-img>
            </div>
            <div class="menu-container-wrapper" :class="{'menu-container-open-width': !openMenuStatus}">
                <div class="menu-container" :class="{'menu-container-open': !openMenuStatus}">
                    <div class="menu-top-container">
                        <div class="header-container">
                            <div class="logo-container">
                                <v-img
                                        src="../assets/images/logo-1.png"
                                        class="logo-img"
                                        max-width="45"
                                ></v-img>
                                <div class="logo-text">al+ <span>minutes</span></div>
                            </div>
                            <div @click="openLeftMenu" :class="{'menu-btn-go-to-left': !openMenuStatus}">
                                <v-img
                                    src="../assets/images/menu-btn-1.png"
                                    class="menu-btn-img"
                                    max-width="16"
                                ></v-img>
                            </div>
                        </div>

                        <div class="menu-title-text">
                            <span>alt group</span>
                        </div>

                        <v-expansion-panels :focusable="focusable" multiple>
                            <v-expansion-panel class="pl-0 mt-1 mb-1" v-for="item in items" :key="item.title">
                                <v-expansion-panel-header disable-icon-rotate class="pa-0 menu-body-color" @click="menuPlusIconChange(item.title)">
                                    <div class="menu-list-title">
                                        <div class="mr-4">
                                            <div :class="`menu-body-icons menu-body-icons${item.icon}`"></div>
                                        </div>
                                        {{item.title }}
                                    </div>
                                    <template v-slot:actions>
                                        <div class="menu-item-right-contant">
                                            <span class="menu-item-count" v-if="item.count">{{item.count}}</span>
                                            <span v-if="item.openStatus">+</span>
                                            <span v-if="!item.openStatus">-</span>
                                        </div>
                                    </template>
                                </v-expansion-panel-header>
                                <v-expansion-panel-content class="pt-3">
                                    Lorem ipsum dolor sit amet
                                </v-expansion-panel-content>
                            </v-expansion-panel>
                        </v-expansion-panels>
                    </div>
                    <div class="menu-bottom-container">
                        <v-img
                                src="../assets/images/icon-Logout.png"
                                class="menu-logout-img"
                                max-width="30"
                        ></v-img>
                        Logout
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "leftSidebar",
        data () {
            return {
                items: [
                    { title: 'Conversation', icon: 'Conversations', openStatus: true, count: '' },
                    { title: 'Group', icon: 'Group', openStatus: true, count: '' },
                    { title: 'Operator', icon: 'Operator', openStatus: true, count: 2 },
                    { title: 'Salespartner', icon: 'Salespartner', openStatus: true, count: 7 },
                    { title: 'alt admin', icon: 'Admin', openStatus: true, count: 4 },
                ],
                right: null,
                openMenuStatus: true,
                focusable: false,
                readonly: false,
            }
        },
        methods: {
            openLeftMenu() {
                this.openMenuStatus = !this.openMenuStatus;
                this.$emit('clicked', this.openMenuStatus);
            },
            menuPlusIconChange(item) {
                this.items.forEach((value) => {
                    if (value.title === item) {
                        value.openStatus = !value.openStatus;
                    }
                });
            }
        },
    }
</script>

<style scoped>
    .sidebar-container {
        display: flex;
        min-height: 100vh;
        height: 100%;
    }
    .sidebar-right-content {
        position: relative;
    }
    .menu-list-title {
        display: flex;
        align-items: center;
    }
    .menu-btn {
        position: absolute;
        background-color: #f7f7f7;
        padding: 10px;
        top: 15px;
        border-radius: 0 10px 10px 0;
        opacity: 0;
        visibility: hidden;
        transition: 0.4s;
    }
    .menu-btn-go-to-right {
        visibility: visible;
        opacity: 1;
    }
    .sidebar-left-content {
        padding: 20px;
        background-color: #f7f7f7;
        min-height: 100vh;
        height: 100%;
        width: 80px;
    }
    .cubo-user {
        width: 40px;
        height: 40px;
        border-radius: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
        cursor: pointer;
    }
    .user-active:after {
        content: '';
        position: absolute;
        top: -8px;
        left: -8px;
        width: 56px;
        height: 56px;
        border: 3px solid #07a766;
        border-radius: 15px;
    }
    .user-online-status {
        position: absolute;
        right: -5px;
        top: -4px;
        background-color: #07a766;
        width: 14px;
        height: 14px;
        border-radius: 50%;
        border: 2.5px solid #f7f7f7;
    }
    .cubo-item-1 {
        background-color: #f0920c;
        color: #fff;
        margin-bottom: 24px;
    }
    .cubo-item-2 {
        background-color: #171932;
        margin-bottom: 24px;
        color: #fff;
    }
    .cubo-item-3 {
        background-image: url("../assets/images/3d566c3de9c892f58efd87a873044a779dfd206d.png");
        background-size: contain;
        background-repeat: no-repeat;
        margin-bottom: 24px;
    }
    .plus-item {
        background-color: #e7e7e7;
        color: #171932;
        font-size: 24px;
        font-weight: 700;
    }
    .cubo-item-1>span {
        font-size: 21px;
        font-weight: bold;
    }
    .cubo-item-2>span {
        font-weight: 100;
        font-size: 24px;
        color: #a0a0a0;
    }
    .cubo-item-3>span {
        color: #fff;
        font-weight: 900;
    }
    .menu-container {
        padding: 50px 30px;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        height: 100%;
        width: 302px;
        transform: translateX(0);
        transition: 0.4s;
        overflow: hidden;
    }
    .menu-container-wrapper {
        height: 100%;
        width: 302px;
        overflow: hidden;
        transition: 0.4s
    }
    .menu-container-open {
        transform: translateX(-100%);
        overflow: visible;
    }
    .menu-container-open-width {
        width: 0;
    }
    .header-container {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .logo-img {
        margin-right: 12px;
    }
    .logo-text {
        font-size: 19px;
    }
    .logo-text>span {
        font-weight: bold;
    }
    .menu-btn-img {
        /*margin-left: 55px;*/
        cursor: pointer;
    }
    .logo-container {
        display: flex;
        align-items: center;
        cursor: pointer;
    }
    .menu-title-text {
        margin: 25px 0 25px 3px;
    }
    .menu-title-text {
        font-size: 24px;
        font-weight: 600;
    }
    .menu-body-color {
        background-color: #fff !important;
    }
    .menu-item-title {
        font-size: 15px !important;
        font-weight: 700 !important;
    }
    .menu-body-icons {
        width: 32px;
        height: 32px;
        background-size: contain;
    }
    .menu-body-iconsConversations {
        background-image: url("../assets/images/icon-Conversations.png");
    }
    .menu-body-iconsGroup {
        background-image: url("../assets/images/icon-Group.png");
    }
    .menu-body-iconsOperator {
        background-image: url("../assets/images/icon-operator.png");
    }
    .menu-body-iconsSalespartner {
        background-image: url("../assets/images/icon_Salespartner.png");
    }
    .menu-body-iconsAdmin {
        background-image: url("../assets/images/icon_admin.png");
    }
    .menu-item-right-contant {
        display: flex;
        align-items: center;
        color: #8d8e98;
        font-weight: 700;
        font-size: 18px;
    }
    .menu-item-count {
        width: 26px;
        height: 26px;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #07a766;
        color: #fff;
        border-radius: 10px;
        font-size: 15px;
        margin-right: 15px;
    }
    .menu-bottom-container {
        display: flex;
        align-items: center;
        cursor: pointer;
        font-size: 17px;
        font-weight: 600;
    }
    .menu-logout-img {
        margin-right: 20px;
    }
</style>
