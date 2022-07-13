<template>
  <NuxtLink :to="link">
    <div
      class="h-28 w-28 bg-primary m-8 rounded-lg flex flex-col justify-center"
    >
      <img
        class="h-12 w-12 mx-auto mb-2"
        :src="require(`~/assets/img/${icon}`)"
        alt=""
      />
      <p class="text-center text-neutral uppercase font-bold">{{ label }}</p>
    </div>
  </NuxtLink>
</template>

<script>
export default {
  props: {
    label: {
      type: String,
      required: true,
    },
    icon: {
      type: String,
      required: true,
    },
    link: {
      type: String,
      required: true,
    },
  },
};
</script>