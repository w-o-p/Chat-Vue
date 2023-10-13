<template>
    <div>
        <div v-if="isAuthorised">
            <div>Добро пожаловать, <b>{{ username }}</b></div>
            <button @click="logout">Выйти</button>
        </div>
        <div v-else>
            <label>Имя:</label>
            <input v-model="username"/>
            <button @click="login">Сохранить</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'HomePage',
    data() {
        return {
            isAuthorised: false,
            username: ''
        }
    },
    created(){
        if (localStorage.getItem('isAuthorised')){
            this.isAuthorised = true;
            this.username = localStorage.getItem('username')
        }
    },
    methods: {
        login(){
            if (this.username != ''){
                console.log(this.username);

                this.isAuthorised = true;
                localStorage.setItem('isAuthorised', true);
                localStorage.setItem('username', this.username);

                this.$router.push({
                    name: 'Chat',
                    query: {username: this.username}
                })
            }
            else {
                console.log('no username')
            }
        },

        logout(){
            this.isAuthorised = false;
            this.username = '';
            localStorage.removeItem('isAuthorised');
            localStorage.removeItem('username');
        }
    }
}
</script>
