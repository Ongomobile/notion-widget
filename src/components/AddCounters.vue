<template>
  <div class="add-counter-form--wrapper">
    <h2 class="add-counter-heading">Add A Counter</h2>
    <!-- prevent modifier prevents default -->
    <form class="add-counter-form" @submit.prevent="addCounter">
      <label for="type" class="add-counter-label" title="add"
        >Counter Name</label
      >
      <input
        type="text"
        id="type"
        name="type"
        class="add-counter-input"
        placeholder="Add Counter Name"
        v-model="windowType"
      />

      <label for="price" class="add-counter-label">Counter Price</label>
      <!-- Use .number modifier to cast input value as number -->
      <input
        type="text"
        id="price"
        name="price"
        class="add-counter-input"
        v-model.number="windowPrice"
        placeholder="Add Window Price"
      />
      <input
        type="submit"
        class="add-counter-input submit"
        value="Add Counter"
        :disabled="isDisabled"
      />
    </form>
    <div class="total-price-wrapper">
      <p class="total-text">Total Price {{ grandTotal || 0.0 }}</p>
      <p>"Feature to be implemented"</p>
    </div>
  </div>
  <div class="counters-wrapper">
    <ul class="counters-list">
      <li
        class="counter-item"
        v-for="(counter, index) in counters"
        :key="index"
      >
        <Counter :counter="counter" />
      </li>
    </ul>
  </div>
</template>

<script>
import Counter from "./Counter.vue";
export default {
  data() {
    return {
      counters: [],
      grandTotal: 0.0,
      windowPrice: "",
      windowType: "",
      quantity: 0,
      counterId: 0,
      subtotal: 0,
    };
  },
  components: {
    Counter,
  },
  methods: {
    addCounter() {
      let newCounter = {
        id: this.counterId + 1,
        windowType: this.windowType,
        windowPrice: this.windowPrice,
        quantity: this.quantity,
        subtotal: this.subtotal,
      };

      if (this.windowPrice !== "" && this.windowType !== "") {
        this.counters.push(newCounter);
      }

      this.windowPrice = "";
      this.windowType = "";
      this.quantity = 0;

      this.counterId = newCounter.id;
      let countersArr = this.counters;
      console.log({ countersArr });
    },
  },
  computed: {
    isDisabled: function () {
      if (this.windowType !== "" && typeof this.windowPrice === "number") {
        return false;
      } else {
        return true;
      }
    },
  },
};
</script>

<style scoped>
.add-counter-form--wrapper {
  display: flex;
  flex-direction: column;
  max-width: 320px;
  margin: 50px auto 30px;
}

.add-counter-form {
  display: flex;
  flex-direction: column;
  padding: 15px;
  border: solid 1px #eee;
  border-radius: 5px;
  margin-bottom: 10px;
  box-shadow: var(--box-shadow);
}

.add-counter-heading {
  margin-bottom: 5px;
  text-align: center;
}

.add-counter-input {
  width: 100%;
  padding-left: 10px;
  border-radius: 5px;
  border: 1px solid #dcdcdc;
  margin-bottom: 10px;
}

.add-counter-label {
  color: #36454f;
  margin-left: 5px;
}

.total-price-wrapper {
  display: flex;
  flex-direction: column;
  padding: 20px;
  box-shadow: var(--box-shadow);
  border-radius: 5px;
}
/* .counters-wrapper {
  padding: 10px;
} */

.counters-list {
  padding: 10px;
  display: flex;
  list-style: none;
  overflow: auto;
  overflow-x: scroll;
}

@media screen and (max-width: 340px) {
  .add-counter-form--wrapper {
    max-width: 295px;
  }
}

/* .counter-item{
  no styles yet
} */
</style>