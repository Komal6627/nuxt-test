<template>
  <div>
    <div class="text-center">
      <h1 class="text-2xl font-bold">Admin Login</h1>
      <form @submit="userLogin">
        <label for="user">Select: </label>

        <select name="user" id="user"  class="border-black border-2 m-1">
          <option value="staf">Staf</option>
          <option value="user">User</option>
        </select>
        <br>
        <label for="name">User Name:</label>
        <input
          type="text"
          id="name"
          v-model="user.name"
          placeholder="Enter the name"
          class="border-black border-2 m-1"
        />
        <br />
        <label for="pass">Password:</label>
        <input
          type="password"
          id="pass"
          v-model="user.password"
          placeholder="Enter the password"
          class="border-black border-2 m-1"
        />
        <br />
        <!-- <button @click="userLogin">Login</button> -->
        <NuxtLink v-slot="{ navigate }" to="/bookSlot" custom>
          <button
            @click="navigate"
            class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-2"
          >
            Book slot
          </button>
        </NuxtLink>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: {
        name: "",
        password: "",
      },
    };
  },
  methods: {
    userLogin(event) {
      event.preventDefault();
      alert("You Logged in");
    },
    bookSlot(event) {
      alert("Your slot is booked");
    },
  },
};
</script>
