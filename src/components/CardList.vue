<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">
        <Card :="item" :onupdate="handleUpdate"></Card>
      </li>
    </ul>
  </div>
</template>
<script>
import Card from './Card.vue';
export default {
  name: 'CardList',
  components: {
    Card,
  },
  data() {
    return {
      shown: false,
      items: [
        {
          id: 1,
          name: 'ナポリタン',
        },
        {
          id: 2,
          name: 'キムチチャーハン',
        },
        {
          id: 3,
          name: '高菜明太マヨ牛丼',
        },
        {
          id: 4,
          name: 'チキン南蛮',
        },
      ],
    };
  },
  methods: {
    showForm() {
      this.shown = true;
    },
    handleUpdate(payload) {
      let idx = -1;
      for (let i = 0; i < this.items.length; i++) {
        if (this.items[i]['id'] === payload.id) {
          idx = i;
        }
      }
      if (idx === -1) {
        return;
      }
      this.items[idx] = payload;
      console.log(this.items);
    },
  },
};
</script>
<style scoped>
li {
  list-style-type: none;
}
</style>
