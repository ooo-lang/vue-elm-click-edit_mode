<template>
  <div class="card-wrapper">
    <div class="card">
      <div class="card-content" @click="editting" v-if="!isEdit">
        {{ name }}
      </div>
      <div class="edit-area" v-if="isEdit">
        <input
          class="edit-input-area"
          v-model="inputValue"
          @keyup.enter="saveContent"
          @keydown.esc="cancelEditing"
        />
        <div class="btn-area">
          <Button @click="saveContent">Edit</Button>
          <Button @click="cancelEditing">Cancel</Button>
        </div>
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
.card-wrapper {
  border: 0.5px solid;
  width: 180px;
  margin-top: 10px;
  padding: 5px;
  padding-bottom: 7px;
  border-radius: 3px;
}
.card {
}
.edit-area {
  margin-top: 5px;
  padding-right: 5px;
  padding-left: 5px;
}
.btn-area {
  display: flex;
  justify-content: center;
}
</style>
