<template>
  <form class="bd-form" novalidate>
    <div>
      <input type="text" v-model="content" placeholder="content..." />
    </div>
    <div>
      <BDButton :disabled="disableAddAction" @click="handleAdd"> Add </BDButton>
      <BDButton :disabled="progress" @click="handleCancel"> Cancel </BDButton>
      <div class="messages">
        <p v-if="progress" class="add-progress">add...</p>
        <p v-if="error" class="add-error">
          {{ error }}
        </p>
      </div>
    </div>
  </form>
</template>
<script>
import BDButton from './Button.vue';
export default {
  name: 'BDForm',
  components: {
    BDButton,
  },
  data() {
    return {
      content: '',
      progress: false,
      error: '',
    };
  },
  computed: {
    disableAddAction() {
      return this.content.length === 0 || this.progress;
    },
  },
  methods: {
    handleAdd() {
      this.progress = true;
      this.error = '';
    },
    handleCancel() {
      this.$emit('close');
    },
  },
};
</script>
<style></style>
