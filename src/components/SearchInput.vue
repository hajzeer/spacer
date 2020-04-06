<template>
    <div class="search">
      <input
        id="search"
        name="search"
        v-model="searchValue"
        @input="handleInput"
      />
    </div>
</template>

<script>
export default {
    name: 'SearchInput',
}
</script>

<style lang="scss" scoped>
.search{
  display: flex;
  flex-direction: column;
  width: 300px;

  input{
    height: 30px;
    border: 0;
    background: none;
    border-bottom: 1.5px solid whitesmoke;
  }
}
</style>