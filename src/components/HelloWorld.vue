<template>
  <div>
    <div>{{ year }} - {{ month + 1 }} - {{ currentDay }}</div>
    <ul class="weekdays">
      <li>日</li>
      <li>一</li>
      <li>二</li>
      <li>三</li>
      <li>四</li>
      <li>五</li>
      <li>六</li>
    </ul>
    <div class="days">
      <div class="item"></div>
    </div>
  </div>
</template>

<script>
import { Group, Cell } from "vux";
Date.prototype.getWeek = function() {
  var janFirst = new Date(this.getFullYear(), 0, 1);
  var today = new Date(this.getFullYear(), this.getMonth(), this.getDate());
  var dayOfYear = (today - janFirst + 1) / 86400000;
  return Math.ceil(dayOfYear / 7);
};

var getDaysOfMonth = (y, m) => {
  return new Date(y, m, 0).getDate();
};

var getDayOfWeek = (y, m, d) => {
  return new Date(y, m, d).getDay();
};


export default {
  components: {
    Group,
    Cell
  },
  data() {
    return {
      days: "",
      year:"",
      month:"",
      currentDay:"",
      daysList: []
    };
  },
  mounted() {
    this.days = '2018-06-18';
    this.getWeek();
  },
  methods: {
    getWeek() {
      let date = new Date(this.days);
      let weekDay = date.getDay();
      this.year = date.getFullYear();
      this.month = date.getMonth();
      this.currentDay = date.getDate();
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
.weekdays {
  li {
    float: left;
    list-style: none;
    margin: 0 20px;
  }
}
</style>
