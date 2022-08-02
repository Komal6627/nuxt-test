<template>
  <div class="">
    <div>
      <button
        class="bg-green-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-2"
        @click="showSlots"
      >
        showSlots
      </button>
    </div>
    <div class="m-1">
      <div
        id="cartBg"
        class="bg-cyan-300 border-4 border-black text-center w-1/4 m-2"
        v-for="item in timeSlots"
        :key="item"
      >
        <div class="font-bold text-xl p-5">Start Time {{ item.startTime }}</div>
        <div class="font-bold text-xl p-5">End Time {{ item.endTime }}</div>
        <div>
          <NuxtLink v-slot="{ navigate }" to="/register" custom>
            <button
              @click="navigate"
              class="bg-black m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-2"
            >
              Book slot
            </button>
          </NuxtLink>
            <!-- <button
              @click="book"
              class="bg-black m-1 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded mt-2"
            >
              Book slot    
            </button> -->
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      timeSlots: [],
    };
  },
  methods: {
    showSlots() {
      var d;
      var e;
      d = new Date("2022-08-01 09:00:00");
      e = new Date("2022-08-01 09:00:00");
      for (let i = 0; i < 20; i++) {
        d.setMinutes(d.getMinutes() + 10);
        e.setMinutes(d.getMinutes() - 10);
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
      document.getElementById("cartBg").style.backgroundColor = "green"

    },
  },
};
</script>

<!--@click="book"-->
