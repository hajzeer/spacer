<template>
    <div class="claim__wrapper">
        <h1 class="claim">SPACER</h1>
        <p class="subclaim">
            Being your journey through our amazing galaxy,
            and discover places you never even heard of.
        </p>
        <p class="subclaim">
            Type anything space-related to start.
        </p>
    </div>
</template>

<script>
export default {
    name: "Claim",
}
</script>

<style lang="scss" scoped>
    .claim__wrapper {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        color: whitesmoke;
    }

    .claim {
        font-size: 50px;
        margin: 0;
    }

    .subclaim {
        margin-top: 25px;
        font-size: 15px;
    }
</style>