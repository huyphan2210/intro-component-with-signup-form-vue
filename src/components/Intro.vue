<template>
    <div class="intro">
        <h1>Learn to code by watching others</h1>
        <p>
            See how experienced developers solve problems in real-time. Watching scripted tutorials is great, 
            but understanding how developers think is invaluable.
        </p>
    </div>
</template>

<style scoped>
.intro {
    color: white;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding: 2rem;
}
    h1 {
        font-size: 3rem;
        line-height: 3.5rem;
    }
@media screen and (max-aspect-ratio: 1 / 1) {
.intro {
    text-align: center;
}
    h1 {
        font-size: 2rem;
        line-height: normal;
    }

    p {
        line-height: 2rem;
    }
}
</style>