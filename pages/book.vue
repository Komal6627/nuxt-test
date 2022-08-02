<template>
  <div class="container mx-auto p-8">
    <h1 class="font-bold text-2xl text-center">Book Slots</h1>
    <main class="flex justify-center w-full h-screen">
      <div>
        <form
          @submit="formSubmit"
          class="bg-cyan-300 border-black rounded-lg border-2 px-12"
        >
          <table>
            <label for="number">Date </label
            >
            <p v-bind="user.date" id="newdate">{{date}}</p>
            <br />
            <!-- <input
              type="date"
              v-model="user.date"
              id="date"
              name="date"
              placeholder="Enter your mobile number"
              required
            /> -->
            <label for="time">Time </label
            ><br />
            <input
              type="time"
              v-model="user.time"
              id="time"
              name="time"
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
                Book Now
              </button>
            </div>
          </table>
        </form>
        <br />
        
        <!-- <div class="flex m-2">
            <div class="border-black bg-gray-100 rounded-lg border-2 p-5 m-4" v-for="(item, index) in users" v-bind:index="index" :key="item">
            <p class="text-lg font-semibold">Slot No:{{ (item.id = index + 1) }}</p>
            <p class="text-lg font-semibold">Name:{{ item.fullname }}</p>
            <p class="text-lg font-semibold">Mobile No:{{ item.number }}</p>
            <p class="text-lg font-semibold">Time:{{ item.time }}</p>  
        </div>
        </div> -->
      </div>
    </main>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      user: {
        date:new Date,
        time: "",
        index: "",
      },
    };
  },
  methods: {
    formSubmit(event) {
      event.preventDefault();
      
      },
    },
  }
</script>
