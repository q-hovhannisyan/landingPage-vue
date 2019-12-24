<template>
    <div class="invite-friends-container">
        <div class="invite-friends-header">
            <v-img
                src="../assets/images/illustration.png"
                class="invite-friends-img"
                max-width="270"
            ></v-img>
            <div class="invite-friends-right-container">
                <div class="invite-friends-title">Invite your friends to enjoy<br> the following benefits:</div>

                <div class="invite-friends-text-bold">For Free Plan Users</div>
                Free trial of standard plan for one month<br>

                <div class="invite-friends-text-bold" style="margin-top: 13px;">For Standard Business Plan Users</div>
                Additional recording time: <span class="invite-friends-color">60 minutes / person</span><br>

                <div style="margin-top: 5px;">Additional number of characters in the translated</div>
                document: <span class="invite-friends-color">10,000 characters / person</span><br>

                <div style="margin-top: 5px;">Additional storage: <span class="invite-friends-color">100MB / person</span></div>
            </div>
        </div>

        <div class="share-via-email-wrapper">
            <div class="share-via-email">Share via email</div>
            <div class="share-via-email-text">Multiple names can be entered with space key or comma</div>
            <div class="share-via-email-container">
                <div class="share-via-email-input-wrapper">
                    <label for="emailAdd" class="share-via-email-input">
                        <div class="all-email-list-container" id="scrollquestion">
                            <div class="email-container" v-for="item in allValue" :key="item">
                                <span>{{item}}</span>
                                <div class="email-delete-btn" @click="deleteEmailInList(item)">
<!--                                    <span class="iconify"  data-inline="false"></span>-->
                                    <v-icon data-icon="mdi-weight">mdi-close</v-icon>
                                </div>
                            </div>
                        </div>
                        <input type="email" id="emailAdd" class="" v-model="inputValue" @keyup.enter="addToMailList">
                    </label>
                </div>
                <div class="share-via-email-button-wrapper">
                    <button class="share-via-email-button">Send Invites</button>
                </div>
            </div>
        </div>

        <div class="social-button-wrapper">
            <div class="social-button" :class="`social-button${item.icon}`" v-for="item in social" :key="item.name">
                <v-icon>{{item.icon}}</v-icon>
                <span>{{item.name}}</span>
            </div>
        </div>

        <div class="referral-link-wrapper">
            <div class="referral-link-title">Share your referral link</div>
            <div class="link-wrapper">
                <div class="link-left-wrapper">
                    <v-icon>mdi-link-variant</v-icon>
                    <span>https://otter.ai/referrals/9CBGLZLS</span>
                </div>
                <a href="" class="copy-link-btn">Copy Link</a>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "inviteFriendsContent",
        data() {
            return {
                social: [
                    {name: 'Share via Facebook', icon: 'mdi-facebook'},
                    {name: 'Share via Twitter', icon: 'mdi-twitter'},
                    {name: 'Share via LinkedIn', icon: 'mdi-linkedin'},
                ],
                inputValue: '',
                allValue: [],
            }
        },
        methods: {
            addToMailList() {
                this.allValue.push(this.inputValue);
                this.inputValue = '';
            },
            remove(arr) {
                var item, arg = arguments, arrLength = arg.length, argPos;
                while (arrLength > 1 && arr.length) {
                    item = arg[--arrLength];
                    while ((argPos= arr.indexOf(item)) !== -1) {
                        arr.splice(argPos, 1);
                    }
                }
                return arr;
            },
            deleteEmailInList(email) {
                this.allValue.forEach((value) => {
                    if (value === email) {
                        this.remove(this.allValue, email);
                    }
                });
            }
        }
    }
</script>

<style scoped>
    .invite-friends-container {
        padding-left: 151px;
    }
    .invite-friends-header {
        display: flex;
        align-items: flex-start;
    }
    .invite-friends-img {
        margin-top: 33px;
    }
    .invite-friends-right-container {
        padding-left: 62px;
        font-size: 15px;
    }
    .invite-friends-title {
        font-size: 24px;
        font-weight: 600;
        margin-bottom: 26px;
        line-height: 1.4;
    }
    .invite-friends-text-bold {
        font-weight: 600;
        margin-bottom: 6px;
    }
    .invite-friends-color {
        color: #07a766;
        font-weight: 600;
    }
    .share-via-email-wrapper {
        margin-top: 74px;
    }
    .share-via-email-text {
        font-size: 13px;
        color: #7d8e9e;
    }
    .share-via-email {
        font-weight: 600;
        margin-bottom: 3px;
        font-size: 17px;
    }
    .share-via-email-container {
        margin-top: 10px;
        display: flex;
    }
    .share-via-email-input-wrapper {
        width: 65%;
    }
    .share-via-email-button-wrapper {
        width: 35%;
    }
    .share-via-email-input {
        width: 100%;
        border: 1px solid #07a766;
        border-radius: 10px;
        padding: 10px 20px;
        height: 60px;
        outline: none;
        display: flex;
        cursor: text;
    }
    .share-via-email-input input {
        outline: none;
    }
    .all-email-list-container {
        display: flex;
    }
    .share-via-email-button {
        width: 142px;
        background-color: #07a766;
        height: 84%;
        margin: 5px 5px 5px 15px;
        border-radius: 10px;
        color: #fff;
        font-size: 15px;
        font-weight: 600;
        outline: none;
    }
    .social-button-wrapper {
        display: flex;
        justify-content: center;
        align-items: center;
        padding-right: 146px;
        margin-top: 55px;
    }
    .social-button {
        padding: 14px 16px;
        display: flex;
        align-items: center;
        background-color: #f5f5f5;
        border-radius: 10px;
        color: #07a766;
        font-weight: 600;
        cursor: pointer;
        height: 50px;
        border: 1px solid transparent;
        transition: .3s;
    }
    .social-button:hover {
        border: 1px solid #07a766;
        background-color: #fff;
    }
    .social-button i {
        color: #07a766;
        margin-right: 9px;
    }
    .social-buttonmdi-twitter {
        margin: 0 15px;
    }
    .referral-link-wrapper {
        margin-top: 52px;
    }
    .referral-link-title {
        font-size: 17px;
        font-weight: 600;
    }
    .link-wrapper {
        display: flex;
        justify-content: space-between;
        margin-top: 9px;
        font-size: 15px;
        margin-right: 154px;
        background-color: #f5f5f5;
        padding: 17px 16px 17px 0;
        border-radius: 10px;
    }
    .link-left-wrapper {
        color: #2b3444;
    }
    .link-left-wrapper i {
        margin: 0 19px;
        color: #b4bec6;
    }
    .copy-link-btn {
        color: #07a766;
        font-weight: 600;
        text-decoration: none;
        transition: 0.4s;
    }
    .copy-link-btn:hover {
        opacity: 0.7;
    }
    .email-container {
        padding: 5px 5px 5px 15px;
        margin-right: 5px;
        background-color: #f7f7f7;
        color: #021a48;
        font-weight: 600;
        border-radius: 10px;
        display: flex;
    }
    .email-container .email-delete-btn i {
        font-size: 18px;
        color: #07a766;
        margin-left: 4px;
    }
    .email-delete-btn {
        cursor: pointer;
    }
    .all-email-list-container {
        max-width: 70%;
        overflow-x: auto;
    }
    .all-email-list-container::-webkit-scrollbar {
        display: none;
    }
</style>
