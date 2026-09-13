<template>
  <div class="user-list">
    <h2>Foydalanuvchilar ro'yxati</h2>
    <ul>
      <li v-for="user in users" :key="user.id">
        {{ user.name }} - {{ user.email }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'UserList',
  data() {
    return {
      users: [
        { id: 1, name: 'Ali Valiyev', email: 'ali@mail.com' },
        { id: 2, name: 'Otabek Toshmatov', email: 'otabek@mail.com' }
      ]
    }
  }
}
</script>

<style scoped>
.user-list {
  padding: 20px;
  font-family: Arial, sans-serif;
}
</style>