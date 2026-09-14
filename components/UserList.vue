<template>
  <div class="crm">
    <aside class="sidebar">
      <div class="logo">CRM</div>

      <div class="menu">
        <div class="menu-item active">Foydalanuvchilar</div>
        <div class="menu-item">Kompaniya</div>
        <div class="menu-item">Mijozlar</div>
      </div>
    </aside>

    <main class="main">
      <header class="header">
        <h2>Foydalanuvchilar</h2>
      </header>

      <section class="content">
        <div class="top">
          <input type="text" placeholder="Qidirish..." class="search" />

          <button class="add-btn">+ Foydalanuvchi qo'shish</button>
        </div>

        <div class="table-box">
          <table>
            <thead>
              <tr>
                <th>#</th>
                <th>Ism</th>
                <th>Email</th>
                <th>Telefon</th>
                <th>Holati</th>
                <th>Amallar</th>
              </tr>
            </thead>

            <tbody>
              <tr v-for="user in users" :key="user.id">
                <td>{{ user.id }}</td>
                <td>{{ user.name }}</td>
                <td>{{ user.email }}</td>
                <td>{{ user.phone }}</td>
                <td>
                  <span class="status">Faol</span>
                </td>
                <td>
                  <button class="edit-btn">O'zgartirish</button>
                  <button class="delete-btn">O'chirish</button>
                </td>
              </tr>
            </tbody>
          </table>
        </div>
      </section>
    </main>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const users = ref([]);

onMounted(async () => {
  const response = await fetch("/api/users");
  users.value = await response.json();
});
</script>

<style scoped>
* {
  box-sizing: border-box;
}

.crm {
  display: flex;
  min-height: 100vh;
  background: #f5f6f8;
  font-family: Arial, sans-serif;
}

.sidebar {
  width: 256px;
  min-height: 100vh;
  background: #ffffff;
  border-right: 1px solid #e5e7eb;
}

.logo {
  height: 64px;
  padding: 22px 24px;
  font-size: 18px;
  font-weight: bold;
  border-bottom: 1px solid #e5e7eb;
}

.menu {
  padding-top: 15px;
}

.menu-item {
  padding: 13px 24px;
  font-size: 14px;
  color: #555;
  cursor: pointer;
}

.menu-item.active {
  background: #eaf5ff;
  color: #1683c7;
}

.main {
  flex: 1;
}

.header {
  height: 64px;
  background: #fff;
  border-bottom: 1px solid #e5e7eb;
  display: flex;
  align-items: center;
  padding: 0 30px;
}

.header h2 {
  font-size: 18px;
  font-weight: 500;
}

.content {
  padding: 30px;
}

.top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 18px;
}

.search {
  width: 280px;
  height: 38px;
  padding: 0 14px;
  border: 1px solid #d5d9de;
  border-radius: 5px;
  outline: none;
}

.add-btn {
  height: 38px;
  padding: 0 18px;
  border: none;
  border-radius: 5px;
  background: #1683c7;
  color: white;
  cursor: pointer;
}

.table-box {
  background: white;
  border: 1px solid #e3e6e8;
  border-radius: 5px;
  overflow: hidden;
}

table {
  width: 100%;
  border-collapse: collapse;
}

th {
  background: #f8f9fa;
  color: #555;
  font-size: 13px;
  font-weight: 500;
  text-align: left;
  padding: 13px 15px;
  border-bottom: 1px solid #e5e7eb;
}

td {
  padding: 13px 15px;
  font-size: 13px;
  color: #444;
  border-bottom: 1px solid #eeeeee;
}

tr:last-child td {
  border-bottom: none;
}

.status {
  color: #159447;
  background: #e9f8ef;
  padding: 4px 9px;
  border-radius: 4px;
  font-size: 12px;
}

.edit-btn {
  border: none;
  background: #1683c7;
  color: white;
  padding: 5px 9px;
  border-radius: 4px;
  font-size: 11px;
  cursor: pointer;
  margin-right: 5px;
}

.delete-btn {
  border: none;
  background: #e5484d;
  color: white;
  padding: 5px 9px;
  border-radius: 4px;
  font-size: 11px;
  cursor: pointer;
}
</style>
