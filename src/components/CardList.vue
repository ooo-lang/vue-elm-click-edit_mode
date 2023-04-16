<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">
        <Card :="item" :onupdate="handleUpdate"></Card>
      </li>
    </ul>
    <Button type="text" @click="showForm" v-if="!shown"
      ><Icon name="add"></Icon
    ></Button>
    <Form v-if="shown" @close="shown = false"></Form>
  </div>
</template>
<script>
import Button from './Button.vue';
import Icon from './Icon.vue';
import Card from './Card.vue';
import Form from './Form.vue';
export default {
  name: 'CardList',
  components: {
    Card,
    Form,
    Button,
    Icon,
  },
  data() {
    return {
      shown: false,
      items: [
        {
          id: 1,
          name: 'ああああ',
        },
        {
          id: 2,
          name: 'いいいい',
        },
        {
          id: 3,
          name: 'うううう',
        },
        {
          id: 4,
          name: 'ええええ',
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
.header {
  background-color: red;
}
</style>
