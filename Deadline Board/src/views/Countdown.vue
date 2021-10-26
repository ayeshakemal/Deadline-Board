<template>
  <div id="app">
    <h1>Deadline Board</h1>

    <InputDeadline @hehe="eventHandler" @haha="messageHandler" />

    <div id="return">
      <h1 id="title">{{ getMessage() }}</h1>
      <p>{{ mounted() }}</p>
      <h2 id="days"></h2>
      <h2 id="othertime"></h2>
      <h2 id="word"></h2>
    </div>
  </div>
</template>

<script>
import moment from "moment";
import InputDeadline from "@/components/InputDeadline.vue";

export default {
  name: "Countdown",
  components: {
    InputDeadline,
  },
  data: function () {
    return {
      // Data properties go here
      date: "",
      final: [],
      timer: null,
      message: "",
    };
  },
  methods: {
    // Methods go here
    eventHandler: function (dat) {
      this.date = dat;
    },

    messageHandler: function (mes) {
      this.message = mes;
    },

    getMessage: function () {
      return this.message;
    },

    updateCountdown: function () {
      var deadline = moment(this.date);
      var now = moment();

      const timeLeft = moment(deadline.diff(now)); // get difference between now and timestamp

      const makeEST = moment(timeLeft, "DDD, HH:mm").subtract(39, "hours");

      if (makeEST.format("DDD") == "365") {
        var days = "0 Days";
      } else {
        days = makeEST.format("DDD [Days]");
      }
      const formatted = makeEST.format(" HH [hrs]: mm [mins]: ss [secs]");
      const word = "Remaining"; // make pretty

      const lis = [days, formatted, word];

      this.final = lis;

      return this.final;
    },

    mounted: function () {
      this.$nextTick(function () {
        var that = this;

        setInterval(function () {
          var timer = that.updateCountdown();

          this.timer = timer;

          if (timer[0] != "Invalid date") {
            document.getElementById("days").innerHTML = timer[0];
            document.getElementById("othertime").innerHTML = timer[1];
            document.getElementById("word").innerHTML = timer[2];
          }
        }, 1000);
      });
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding-left: 30px;
  padding-right: 30px;
}
#return {
  border: solid 1px;
  padding-top: 30px;
  width: 40%;
  height: 280px;
  margin-right: 20px;
  margin-top: 20px;
  padding-bottom: 30px;
}

#days {
  text-align: center;
  font-size: 40px;
}

#othertime {
  text-align: center;
}

#title {
  text-align: center;
}
#elements {
  display: block;
}

#right {
  display: block;
  float: right;
  width: 50%;
}
body {
  min-width: 950px;
}
</style>
