<template>
      <div>
            <label :for="label"> {{ label }} </label>
            <input :id="label" :type="type" :required="required" v-model="value" />
      </div>
</template>

<script>
export default {
      props: {
            label: {
                  type: String,
                  required: true,
            },
            type: {
                  type: String,
                  required: true,
            },
            modelValue: {
                  type: String,
                  required: true,
            },
            required: {
                  type: Boolean,
                  default: true,
            },
      },
      data() {
            return {};
      },

      computed: {
            value: {
                  get() {
                        return this.modelValue;
                  },
                  set(value) {
                        this.$emit("update:modelValue", value);
                  },
            },
      },
};
</script>

<style></style>
