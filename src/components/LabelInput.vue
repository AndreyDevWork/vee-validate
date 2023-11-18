<template>
  <div class="wrapper">
    <label class="label" :for="name">{{ label }}
      <span class="required" v-if="required">*</span>
    </label>
    <slot/>
  </div>
</template>

<script>
export default {
  name: 'LabelInput',
  props: {
    name: String,
    label: String,
    required: {
      type: Boolean,
      default: false
    }
  }
}
</script>

<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    row-gap: 12px;
  }
  .label {
    font-size: 14px;
    font-weight: 500;
    line-height: 100%;
    color: var(--header-title);
  }
  .required {
    color: red;
  }
</style>