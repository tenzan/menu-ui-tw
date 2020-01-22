<template>
  <div>
    <table
      class="table-auto"
      v-for="item in menuItems"
      :key="item.name"
      :class="item.highlight ? 'highlight' : ''"
    >
      <tr>
        <td class="border px-4 py-2 text-justify">
          {{ item.name }} {{ item.price }}
        </td>
        <td class="border px-4 py-2 text-right">{{ item.price }}</td>
      </tr>
    </table>
  </div>
</template>
<script>
export default {
  data() {
    return {
      menuItems: [
        {
          name: "Apple",
          price: 20,
          image_url: "../assets/images/apple.jpg"
        },
        {
          name: "Orange",
          price: 21,
          image_url: "../assets/images/orange.jpg"
        },
        {
          name: "Banana",
          price: 22,
          image_url: "../assets/images/banana.jpg"
        },
        {
          name: "Grape",
          price: 23,
          image_url: "../assets/images/grape.jpg"
        }
      ]
    };
  },
  created() {
    var self = this;
    self.menuItems.map((x, i) => {
      self.$set(self.menuItems[i], "highlight", false);
    });
    var init = 0;
    setInterval(function() {
      if (init === self.menuItems.length) {
        init = 0;
      }
      self.menuItems[init].highlight = true;
      if (init === 0) {
        self.menuItems[self.menuItems.length - 1].highlight = false;
      } else {
        self.menuItems[init - 1].highlight = false;
      }
      init++;
    }, 2000);
  }
};
</script>

<style scoped>
.highlight {
  background-color: grey;
  font-weight: 900;
}
</style>
