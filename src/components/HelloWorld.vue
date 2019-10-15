<template>
  <div>
    <p>Spaces Left: {{ spaceLeft }} outof {{ capacity }} </p>
    <h2>Attending</h2>
    <ul>
      <li v-for="(name, index) in attending" :key="index">
        {{ name }}
      </li>
    </ul>
    <button @click="increaseCapacity">Increase Capacity</button>
  </div>
</template>

<script>
import { ref, computed, reactive, toRefs } from '@vue/composition-api';

export default {
  // setup() {
  //   const capacity = ref(4);
  //   console.log(capacity);
  //   const attending = ref(["Tim", "Bob", "Joe"]);
  //   const spaceLeft = computed(() => {
  //     return capacity.value - attending.value.length;
  //   })
  //   function increaseCapacity() {
  //     capacity.value++;
  //   }
  //   return { capacity, attending, spaceLeft, increaseCapacity }
  // }  


  // can also be written as


  setup() {
    const event = reactive({
      capacity: 4,
      attending: ["Tim", "Bob", "Joe"],
      spaceLeft: computed(() => { return event.capacity - event.attending.length; })
    })
    function increaseCapacity() {
      event.capacity++;
    }
    // toRefs creates a plain object with reactive references
    return { ...toRefs(event), increaseCapacity }
  }
}
</script>

<style>
</style>
