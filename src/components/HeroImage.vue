<template>
    <div class="HeroImage" />
</template>

<script>
export default {
  name: 'HeroImage',
};
</script>

<style lang="scss" scoped>
.HeroImage {
    position: fixed;
    width: 100%;
    height: 100vh;
    z-index: -1;
    top: 0;
    background-image: url('../assets/heroimage.jpg');
    background-repeat: no-repeat;
    background-size:cover;
    background-position: 80% 0%;
}

.HeroImage::after {
    content: '';
    background: rgba(0, 0, 0, .2);
    position: absolute;
    top: 0;
    left: 0;
    z-index: 1;
    width: 100%;
    height: 100vh;
}
</style>
