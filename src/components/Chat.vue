<template>
    <div>
        <div v-if="username">
            <div class="chat">
                <h2>Чат</h2>
                <div class="text" v-for="message in messages" :key="message.id">
                    <b>{{ message.user }}</b>: {{ message.text }}
                </div>
                <div v-show="emptyMsg" class="empty">Сообщений пока нет</div>
            </div>
            <input placeholder="Введите сообщение" v-model="newMessage"/>
            <button @click="sendMessage">Отправить</button>
            <button @click="delMessage">Удалить</button>
        </div>
        <div v-else>
            <router-link :to='{name: "Home"}'>Требуется авторизация</router-link>
        </div>
    </div>
</template>

<script>

export default {
    name: 'ChatComp',
    data(){
        return {
            messages: [],
            newMessage: '',
            emptyMsg: true,
            username: localStorage.getItem('username')
        }
    },
    computed() {
        localStorage.setItem('username', this.username)
    },
    methods: {
        sendMessage(){
            if (!this.username){
                this.username = 'Anonymous';
            }
            if (this.newMessage != ''){
                this.emptyMsg = false;
                this.messages.push({id: new Date().getTime(), text: this.newMessage, user: this.username});
                this.saveChatRecords();
                this.newMessage = '';
            }
            else {
                alert('Введите сообщение')
            }
        },
        saveChatRecords(){
            const records = this.messages;
            localStorage.setItem(`messages_${this.username}`, JSON.stringify(records));
        },
        delMessage(){
            this.messages = [];
            localStorage.removeItem(`messages_${this.username}`, JSON.stringify(this.message));
            this.emptyMsg = true;
        },
        loadChatRecords(){
            const records = JSON.parse(localStorage.getItem(`messages_${this.username}`))
            if (records){
                this.messages = records;
                this.emptyMsg = false;
            }
        },
    },
    created(){
        this.loadChatRecords();
    }
}
</script>

<style>
.chat{
    margin-bottom: 10px;
}
</style>
