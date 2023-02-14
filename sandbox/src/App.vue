<script>
export default {
  data() {
    return {
      count: 0,
      counterTitle: "Counter Standard",
      message: "Hello it works!",
      incrementAmount: 5,
      listOfNumbers: [
        {
          name: 1,
          id: "9e2c1a56-1f1e-4d71-9156-28916bd64585",
          list: [1, 2, 3],
        },
        {
          name: 2,
          id: "c2f2df3f-b827-4ef7-9cde-c04bc3b7f4f9",
          list: [1, 2, 3],
        },
        {
          name: 3,
          id: "57198b45-8f63-410b-b29d-815bf79d2bbf",
          list: [1, 2, 3],
        },
        {
          name: 4,
          id: "e47367d9-bdad-4070-ac11-58a052dbb0fa",
          list: [1, 2, 3],
        },
      ],
    };
  },
  computed: {
    displayTitle() {
      if (this.count > 20) {
        return "Counter Standard Very Long";
      } else {
        return "Counter Standard";
      }
    },
    optimizeIncrementAmount() {
      return this.displayTitle.length * this.incrementAmount;
    },
  },
  methods: {
    incrementCount(newAmount, event) {
      this.count += this.optimizeIncrementAmount;
    },
  },
  watch: {
    count(newValue) {
      if (newValue > 20) {
        this.counterTitle += " Very Long";
      }
    },
  },
}
</script>

<template>
  <h1>Hello frontend Masters!</h1>
  <h1>{{ displayTitle }}</h1>
  <p :data-increment-by="incrementAmount">{{ count }}</p>
  <button @click="incrementCount">Increment Count</button>

  <h1> {{ incrementAmount }}</h1>
  <p>{{ optimizeIncrementAmount }}</p>
  <div>
    <label for="">Increment by: </label>
    <input type="number" v-model="incrementAmount" />
  </div>
  <hr />
  <p v-if="message.length % 2 === 0">Even: {{ message.toUpperCase() }}</p>
  <p v-else>Odd: {{ message }}</p>

  <ul v-for="(item, index) in listOfNumbers" :key="`item-${index}`">
    <li>
      {{ item.id }}
      <ul>
        <li v-for="(number, index) in item.list" :key="`number-${index}`">
          {{ number }}
        </li>
      </ul>
    </li>
  </ul>
  <hr />
</template>
