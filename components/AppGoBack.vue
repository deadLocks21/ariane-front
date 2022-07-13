<template>
  <div class="py-6">
    <div class="h-8">
      <div
        class="flex flex-auto w-fit py-6 pl-4 fixed top-0 left-0"
        @click="$router.go(-1)"
      >
        <img
          class="h-8 w-8 mr-2"
          :src="require(`~/assets/img/previous.png`)"
          alt="Go back button"
        />
        <span class="uppercase text-xl font-bold">Retour</span>
      </div>
    </div>
  </div>
</template>