<template>
  <div class="container mx-auto p-8">
    <h1 class="font-bold text-2xl text-center">Contact Details</h1>
    <main class="flex justify-center w-full h-screen">
      <div>
        <form
          @submit="formSubmit" 
          class="bg-cyan-300 border-black rounded-lg border-2 px-12"
        >
          <table>
            <label class="pt-10 py-10" for="fullname">Name:</label
            ><br />
            <input
              type="text"
              v-model="user.fullname"
              id="fullname"
              name="fullname"
              placeholder="Enter your Full name"
              required
            /><br /><br />
            <label for="number">Mobile Number: </label
            ><br />
            <input
              type="number"
              v-model="user.number"
              id="number"
              name="number"
              placeholder="Enter your mobile number"
              required
            />
            <br /><br />
            <div>
              <!-- <button class="py-1 px-5 mr-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3" type="submit" @click="formSubmit" > Book Now </button> -->
              <button
                class="py-1 px-5 mr-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3"
                type="submit"
                @click="formSubmit"
              >
                Submit
              </button>

              <button
                class="py-1 px-5 bg-black hover:bg-blue-400 text-white font-bold text-center rounded-md mb-3"
                type="reset"
              >
                Reset
              </button>
            </div>
          </table>
        </form>
        <br />

        <div class="flex m-2">
          <div
            class="border-black bg-gray-100 rounded-lg border-2 p-5 m-4"
            v-for="(item, index) in users"
            v-bind:index="index"
            :key="item"
          >
            <p class="text-lg font-semibold">
              Slot No:{{ (item.id = index + 1) }}
            </p>
            <p class="text-lg font-semibold">Name:{{ item.fullname }}</p>
            <p class="text-lg font-semibold">Mobile No:{{ item.number }}</p>
            <p>
              {{ item.Action }}
              <button
                class="mx-3 my-2 p-1 rounded-lg bg-green-600 hover:bg-green-600 text-white w-20"
                @click="onEdit(index)"
              >
                Edit
              </button>
            </p>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isEdit: false,
      indexEdit: -1,
      users: [],
      user: {
        fullname: "",
        number: "",
        time: "",
      },
    };
  },
  methods: {
    formSubmit(event) {
      event.preventDefault();
      if (this.isEdit == true) {
        this.users[this.indexEdit] = this.user;
        this.isEdit = false;
        this.indexEdit = -1;
      } else {
        // if (this.users[index] == 20) {

        //     this.users.push(this.user);
        // }
        // else{
        //     alert("Sorry  no slot availabel")
        // }
        this.users.push(this.user);
        alert("Your data is added");
      }

      this.user = {
        fullname: "",
        number: "",
      };
    },
    onReset(event) {
      event.preventDefault();
      this.form.name = "";
      this.form.contact = "";
    },
    onEdit(index) {
      this.user.fullname = this.users[index].fullname;
      this.user.number = this.users[index].number;
      this.isEdit = true;
      this.indexEdit = index;
    },
  },
};
</script>
