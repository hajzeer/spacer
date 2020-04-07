<template>
    <div :class="[{ flexStart: step === 1}, 'wrapper']">
      <transition name="slide">
        <img src="./assets/logo.svg" class="logo" v-if="step === 1">
      </transition>
      <transition name="fade">
        <HeroImage v-if="step === 0"/>
      </transition>
      <Claim v-if="step === 0" />
      <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
    </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';

import Claim from './components/Claim.vue';
import SearchInput from './components/SearchInput.vue';
import HeroImage from './components/HeroImage.vue';

const API = 'https://images-api.nasa.gov/search';


export default {
  name: 'App',
  data() {
    return {
      loading: false,
      step: 0,
      searchValue: '',
      resoults: [],
    };
  },
  components: {
    Claim,
    SearchInput,
    HeroImage,
  },

  methods: {
    handleInput: debounce(function () {
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.resoults = response.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 1000),
  },
};
</script>
<style lang="scss">

*{
  box-sizing: border-box;
}

body{
  font-family: 'Montserrat', sans-serif;
  margin: 0;
  padding: 0;
}

.wrapper{
  margin: 0;
  position: relative;
  width: 100%;
  min-height: 100vh;
  padding: 30px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  &.flexStart {
    justify-content: flex-start;
  }
}

.fade-enter-active, .fade-leave-active {
  transition: opacity .3s ease;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}

.logo {
  position: absolute;
  top: 30px;

}

.slide-enter-active, .slide-leave-active {
  transition: margin-top .3s ease;
}

.slide-enter, .slide-leave-to {
  margin-top: -50px;
}
</style>
