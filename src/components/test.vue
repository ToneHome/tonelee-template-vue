<template>
  <div>
      <div  v-for="item in lists">
          <input v-if="item.type == 'input'" v-modal="" type="text">
      </div>
  </div>
</template>

<script>
export default {
  components: {},
  data() {
    return {
      lists: []
    };
  },
  mounted() {
    this.lists = [
      {
        tpye: "input",
        name: "name",
        value: ""
      },
      {
        tpye: "input",
        name: "age",
        value: ""
      },{
        tpye: "input",
        name: "sex",
        value: ""
      },{
        tpye: "input",
        name: "id",
        value: ""
      }
    ];
  },
  methods: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
</style>
