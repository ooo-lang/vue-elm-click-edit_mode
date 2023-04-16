<template>
  <div>
    <div class="contaner">
      <div @click="editting" v-if="!isEdit">
        {{ name }}
      </div>
      <div v-if="isEdit">
        <input
          v-model="inputValue"
          @keyup.enter="saveContent"
          @keydown.esc="cancelEditing"
        />
        <Button @click="saveContent">Edit</Button>
        <Button @click="cancelEditing">Cancel</Button>
      </div>
    </div>
  </div>
</template>
<script>
import Button from './Button.vue';
export default {
  name: 'card',
  components: {
    Button,
  },
  data() {
    return {
      isEdit: false,
      inputValue: '',
    };
  },
  props: {
    id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    onupdate: {
      type: Function,
      required: true,
    },
  },
  methods: {
    editting() {
      this.isEdit = true;
      this.inputValue = this.name;
    },
    saveContent() {
      this.onupdate({ id: this.id, name: this.inputValue });
      this.isEdit = false;
    },
    cancelEditing() {
      this.isEdit = false;
    },
  },
};
</script>
<style scoped>
.contaner {
  display: flex;
  margin: 5px;
}
</style>
