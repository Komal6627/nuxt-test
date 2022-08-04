<template>
  <div>
    <button
      class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-2"
      @click="showSlots"
    >
      showSlots
    </button>
    <div class="m-1 flex flex-wrap">
      <div
        class="bg-green-400 border-4 border-black text-center w-1/4 m-2"
        v-for="item in timeSlots"
        :key="item"
        id="idx"
      >
        <div>
          <div
            class="text-center"
            v-for="(item, index) in users"
            v-bind:index="index"
            :key="item"
          >
            <p class="text-lg font-semibold">
              Slot No:{{ (item.id = index + 1) }}
            </p>
            <p class="text-lg font-semibold">Name:{{ item.fullname }}</p>
            <p class="text-lg font-semibold">Mobile No:{{ item.number }}</p>
          </div>
        </div>

        <div class="font-bold text-xl p-5">Start Time {{ item.startTime }}</div>
        <div class="font-bold text-xl p-5">End Time {{ item.endTime }}</div>
        <button
          class="bg-black text-white font-bold py-2 px-4 rounded mb-1"
          @click="book"
        >
          <label for="fullname"> Book Now </label>
        </button>
      </div>

      <div v-if="formshow == true" class="container mx-auto p-8">
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
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      timeSlots: [],
      isEdit: false,
      formshow: false,
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
    showSlots() {
      var d;
      var e;
      d = new Date("2022-08-01 09:00:00");
      e = new Date("2022-08-02 08:50:00");
      for (let i = 0; i < 20; i++) {
        d.setMinutes(d.getMinutes() + 10);
        e.setMinutes(e.getMinutes() + 10);
        // console.log(d);
        this.timeSlots.push({
          startTime: e.toLocaleTimeString(),
          endTime: d.toLocaleTimeString(),
        });
      }
      console.log(d);
    },
    book() {
      alert("Your slot is booked");
      document.getElementById("idx").style.backgroundColor = "red";

      this.formshow = true;
    },
    formSubmit(event) {
      event.preventDefault();
      if (this.isEdit == true) {
        this.users[this.indexEdit] = this.user;
        this.isEdit = false;
        this.indexEdit = -1;
      } else {
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

<!--@click="book"-->
