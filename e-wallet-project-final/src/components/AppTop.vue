<template>
    <div>
        
        <h1>{{ title }}</h1>
        <p>{{ cardTitle }}</p>

    </div>
</template>

<script>
export default {

    props: {

        title: {

            type: String,
            required: true
        },

        cardTitle: {

            type: String,
            required: true
        }
    }

}
</script>

<style lang="scss" scoped>

h1 {
    font-size: 4rem;
}

p {
    font-size: 1.3rem;
    color: rgb(173, 170, 170);
}
</style>