
<template>
  <div id="dateInput">
    <div id="boxes">
      <div id="leftbox">
        <h3>High Priority:</h3>
      </div>

      <div id="middlebox">
        <h3>Medium Priority:</h3>
      </div>

      <div id="rightbox">
        <h3>Low Priority:</h3>
      </div>
    </div>
    <br />

    <div id="form wrap">
      <div id="left">
        <h4>No deadlines yet. Enter one below to display.</h4>
        <form>
          <input type="text" v-model="announce" required />
          <br />
          <br />
          <input
            type="date"
            v-model="dateFromField"
            max="2022-09-15"
            min="2021-09-17"
            required
          />
          <br />
          <br />
          <input type="button" @click="send()" value="Input Deadline" />
        </form>
      </div>

      <div id="right">
        <form>
          <input
            type="button"
            id="button-left"
            @click="incrementValue()"
            value="∧"
          />
          <input
            type="button"
            id="button-right"
            @click="decrementValue()"
            value="∨"
          />
          <input type="text" id="number" value="0" />
          <label>High Priority Tasks</label>
        </form>
        <form>
          <input
            type="button"
            id="button-left"
            @click="incrementValue2()"
            value="∧"
          />
          <input
            type="button"
            id="button-right"
            @click="decrementValue2()"
            value="∨"
          />
          <input type="text" id="number2" value="0" />
          <label>Medium Priority Tasks</label>
        </form>

        <form>
          <input
            type="button"
            id="button-left"
            @click="incrementValue3()"
            value="∧"
          />
          <input
            type="button"
            id="button-right"
            @click="decrementValue3()"
            value="∨"
          />

          <input type="text" id="number3" value="0" />

          <label>Low Priority Tasks</label>
        </form>
      </div>
    </div>
  </div>
</template>



<script>
import moment from "moment";
export default {
  name: "InputDeadline",
  data: function () {
    return {
      // Data properties go here.
      announce: "",
      dateFromField: Date,
    };
  },
  methods: {
    send() {
      let newDate = new Date(this.dateFromField);
      newDate.setDate(newDate.getDate() + 1);
      newDate = moment(newDate);

      this.$emit("hehe", newDate);
      this.$emit("haha", this.announce);

      var x = document.getElementById("left");
      if (x.style.display === "none") {
        x.style.display = "block";
      } else {
        x.style.display = "none";
      }
    },

    incrementValue: function () {
      var value = parseInt(document.getElementById("number").value, 10);
      value = isNaN(value) ? 0 : value;
      value++;
      document.getElementById("number").value = value;
    },

    incrementValue2: function () {
      var value = parseInt(document.getElementById("number2").value, 10);
      value = isNaN(value) ? 0 : value;
      value++;
      document.getElementById("number2").value = value;
    },

    incrementValue3: function () {
      var value = parseInt(document.getElementById("number3").value, 10);
      value = isNaN(value) ? 0 : value;
      value++;
      document.getElementById("number3").value = value;
    },

    decrementValue: function () {
      var value = parseInt(document.getElementById("number").value, 10);
      value = isNaN(value) ? 0 : value;
      value--;
      document.getElementById("number").value = value;
    },
    decrementValue2: function () {
      var value = parseInt(document.getElementById("number2").value, 10);
      value = isNaN(value) ? 0 : value;
      value--;
      document.getElementById("number2").value = value;
    },
    decrementValue3: function () {
      var value = parseInt(document.getElementById("number3").value, 10);
      value = isNaN(value) ? 0 : value;
      value--;
      document.getElementById("number3").value = value;
    },
  },
};
</script>

<style>
#formm {
  text-align: left;
  width: 50%;
}

#formm form {
  width: 300px;
}

#formm h4 {
  width: 300px;
}

h4 {
  text-align: center;
}

input {
  border: 1px solid black;
  border-radius: 3px;
  padding: 10px;
  font-size: 20px;
}

button {
  border: 1px solid black;
  border-radius: 3px;
  padding: 10px;
  margin-left: 15px;
  font-size: 20px;
}
#boxes {
  display: block;
  height: 280px;
}

#leftbox {
  float: left;
  background: hsl(0, 77%, 70%);
  width: 33.3333%;
  height: 280px;
}
#middlebox {
  float: left;
  background: rgb(250, 232, 131);
  width: 33.3333%;
  height: 280px;
}
#rightbox {
  float: right;
  background: #9eff91;

  width: 33.33333%;
  height: 280px;
}

#formwrap {
  display: block;
  height: 280px;
}

#left {
  float: left;
  border: solid 1px;
  padding-top: 30px;
  width: 40%;
  height: 280px;
  margin-right: 20px;
  margin-top: 20px;
  padding-bottom: 30px;
}
#right {
  float: right;

  padding-top: 90px;
  padding-bottom: 0px;
  margin: 20px;

  width: 40%;
  height: 280px;
}

#right form {
  text-align: left;
  padding-left: 50px;
  padding-bottom: 15px;
}

#number {
  width: 50px;
  margin-right: 20px;
}
#number2 {
  width: 50px;
  margin-right: 20px;
}
#number3 {
  width: 50px;
  margin-right: 20px;
}

#button-left {
  background-color: #bae5f7;
  margin-right: 10px;
}
#button-right {
  background-color: #bae5f7;
  margin-right: 10px;
}
</style>
