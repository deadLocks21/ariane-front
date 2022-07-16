<template>
  <div class="w-screen h-screen">
    <div
      class="
        h-2/6
        bg-[url('/assets/img/header.jpg')] bg-cover bg-center
        rounded-br-lg rounded-bl-lg
      "
    ></div>
    <div class="h-4/6 pt-6 flex flex-col">
      <p class="text-center text-xl mt-6">
        Temps passé depuis la dernière tété
      </p>
      <p class="text-center text-xl font-bold">{{ last_feed_since }}</p>
      <div
        class="buttons flex flex-col flex-auto items-center justify-center pb-8"
      >
        <div class="flex justify-around">
          <AppButtonSquare label='Tétés' icon="feeding-bottle.png" link="/feeding-bottle" />
          <AppButtonSquare label='Couches' icon="diaper.png" link="/diaper" />
        </div>
        <AppButtonSquare label='Historique' icon="history.png" link="/history" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",
  data() {
    return {
      last_feed_since: "",
      interval_id: 0,
      start: this.$moment(),
    };
  },
  created() {
    this.interval_id = setInterval(
      function () {
        this.last_feed_since = this.format(
          this.$moment().diff(this.start, "seconds")
        );
      }.bind(this),
      500
    );
  },
  beforeDestroy() {
    clearInterval(this.interval_id);
  },
  methods: {
    format(initial) {
      const hours = Math.floor(initial / 3600);
      initial -= hours * 60;
      const minutes = Math.floor(initial / 60);
      initial -= minutes * 60;
      const seconds = initial;

      return (
        this.twoDigit(hours) +
        ":" +
        this.twoDigit(minutes) +
        ":" +
        this.twoDigit(seconds)
      );
    },
    twoDigit(value) {
      return value < 10 ? `0${value}` : value;
    },
  },
};
</script>
