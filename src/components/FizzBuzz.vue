<script lang="ts">
import { defineComponent } from "vue";

type FizzBuzzItem = {
  key: number;
  value: string;
};

export default defineComponent({
  setup() {
    const range: FizzBuzzItem[] = [];

    const initRange = () => {
      for (const key of Array(100).keys()) {
        range.push({
          key: key,
          value: getFizzBuzzValue(key + 1),
        });
      }
    };

    const getFizzBuzzValue = (key: number): string => {
      if (key % 3 === 0 && key % 5 === 0) {
        return "FizzBuzz";
      }
      if (key % 3 === 0) {
        return "Fizz";
      }
      if (key % 5 === 0) {
        return "Buzz";
      }
      return key.toString();
    };

    initRange();

    return {
      range,
    };
  },
});
</script>

<template>
  <div>
    <h1>FizzBuzz Challenge</h1>
    <ul>
      <li v-for="item in range" :key="item.key">{{ item.value }}</li>
    </ul>
  </div>
</template>

<style scoped></style>
