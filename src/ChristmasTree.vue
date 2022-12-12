<template>
  <div>
    <slot v-if="array.length === 1" v-bind:item="array[0]">
      <div class="flex flex-row justify-center">
        <!-- This div is styled for the tree sections, but it's not complete -->
        <div class="relative rounded-full bg-green w-16 h-16 -m-2 flex justify-center items-center" />
      </div>
    </slot>

    <ChristmasTree v-else :size="size - 1">
      <template v-slot="{ item }">
        <div class="flex flex-row justify-center">
          <!-- This div is styled for the tree sections, but it's not complete -->
          <div class="relative rounded-full bg-green w-16 h-16 -m-2 flex justify-center items-center"
            v-for="n in size" />
        </div>
        <slot v-bind:item="item" />
      </template>
    </ChristmasTree>
  </div>
</template>

<script setup>
const props = defineProps({
  size: Number
})

const array = Array.from(Array(props.size + 1).keys(), item => item + 1);
</script>
