<template>
    <input
      id="search"
      name="search"
      :class="{ dark }"
      :value="value"
      @input="handleChange"
    />
</template>

<script>
export default {
  name: 'SearchInput',

  props: {
    value: {
      type: String,
      required: true,
    },

    dark: {
      type: Boolean,
      defoult: false,
    },
  },

  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
input{
  margin-top: 40px;
  display: flex;
  width: 300px;
  border: 0;
  background: none;
  border-bottom: 1.5px solid whitesmoke;
  color: whitesmoke;
  text-align: center;
  font-size: 17px;
  font-weight: 400;
  transition: box-shadow .3s ease-out;

  @media (min-width: 1024px) {
    font-size: 20px;
  }
}

input:focus {
  outline: none;
  box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .4);
}

.dark {
  background: none;
  color: black;
  border-bottom-color: black;
}

.dark:focus {
  outline: none;
  background: none;
  box-shadow: 0 10px 20px -8px rgba(0, 0, 0, .4);
}
</style>
