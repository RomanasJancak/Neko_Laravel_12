<template>
  <div class="p-4">
    <h2 class="text-xl font-bold mb-4">All Users</h2>
    <table class="w-full border-collapse border border-gray-300">
      <thead>
        <tr class="bg-gray-100">
          <th class="border p-2">ID</th>
          <th class="border p-2">Name</th>
          <th class="border p-2">Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <td class="border p-2">{{ user.id }}</td>
          <td class="border p-2">{{ user.name }}</td>
          <td class="border p-2">{{ user.email }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "UserList",
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    fetch("/api/users")
      .then((res) => res.json())
      .then((data) => {
        this.users = data;
      })
      .catch((err) => {
        console.error("Failed to fetch users:", err);
      });
  },
};
</script>
