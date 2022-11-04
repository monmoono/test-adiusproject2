<template>
  <div class="hello">
    <div class="grid-container">
      <div class="item1">Welcom to website <i class="fa fa-car"></i></div>
      <div class="item2">
        <h1 class="text-h">Meet our leadership</h1>
        <p class="textp">
          Libero fames augue nisl porttitor nisi,quis. Id ac elit odio vitae
          elementum enim vitae ullamcorper suspendisse.Vivamus fringilla.
        </p>
      </div>
      <div class="item3">
        <tbody v-for="(item, index) in items" :key="index">
          <tr>
            <td><img :src="item.avatar" /></td>
            <td>{{ item.first_name + "" + item.last_name }}</td>
            <td>{{ item.email }}</td>
          </tr>
        </tbody>
      </div>
      <div class="item4">Right</div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "App",
  data: () => ({
    items: [],
  }),
  created() {
    axios.get("https://reqres.in/api/users").then((resp) => {
      let lg = resp.data.data;
      var arr = [];
      for (let i = 0; i < lg.length; i++) {
        var obj = {};
        obj = {
          id: resp.data.data[i].id,
          email: resp.data.data[i].email,
          first_name: resp.data.data[i].first_name,
          last_name: resp.data.data[i].last_name,
          avatar: resp.data.data[i].avatar,
        };
        arr.push(obj);
      }
      this.items = arr;
      console.log(arr);
    });
  },
};
</script>

<style lang="scss" scoped>
.item1 {
  grid-area: header;
}
.item2 {
  grid-area: menu;
}
.item3 {
  grid-area: main;
}
.item4 {
  grid-area: right;
}

.grid-container {
  display: grid;
  grid-template-areas:
    "header header header header header header"
    "menu main main main right right";
  gap: 10px;
  background-color: #2196f3;
  padding: 10px;
}

.grid-container > div {
  background-color: rgba(255, 255, 255, 0.8);
  text-align: center;
  padding: 20px 0;
  font-size: 30px;
}
</style>
