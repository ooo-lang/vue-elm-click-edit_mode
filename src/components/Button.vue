<template>
  <button
    :class="classes"
    :disabled="disabled"
    type="button"
    @click="handleClick"
  >
    <slot />
  </button>
</template>
<script>
export default {
  name: 'BDButton',
  emits: ['click'],
  props: {
    type: {
      type: String,
      default: 'button',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    classes() {
      const cls = this.type === 'text' ? '-' + this.type : '';
      return [`Bd-button${cls}`];
    },
  },
  methods: {
    handleClick(ev) {
      this.$emit('click', ev);
    },
  },
};
</script>
<style scoped></style>
