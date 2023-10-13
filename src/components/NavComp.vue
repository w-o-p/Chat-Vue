<template>
    <div class="nav-container">
        <nav>
            <router-link to="/">Домашняя страница</router-link>
            <router-link to="/chat">Чат</router-link>
            <router-link to="/test">Подгрузка данных</router-link>
        </nav>
    </div>
</template>

<script>
export default{
    name: 'NavComp'
}
</script>

<style>
.nav-container{
  margin-bottom: 20px;
  background: red;
}

nav {
  width: 500px;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  margin: 50px;
}
a{
  color: white;
  text-decoration: none;
}
</style>