<template>

<div class="card-wrapper">

    <div class="card" :class="cardColor" >

        <img v-if="this.card.vendor === 'Ninja-bank'" class="vendor-chip" src="../assets/chip-light.svg" alt="chip">
        <img v-else src="../assets/chip-dark.svg" class="vendor-chip" alt="chip">

        <img v-if="this.card.vendor === 'bitcoin-inc'" class="vendor-logo" src="../assets/vendor-bitcoin.svg" alt="logo" />
        <img v-else-if="this.card.vendor === 'Ninja-bank'" class="vendor-logo" src="../assets/vendor-ninja.svg" alt="logo" />
        <img v-else-if="this.card.vendor === 'Block-chain-INC'" class="vendor-logo" src="../assets/vendor-blockchain.svg" alt="logo" />
        <img v-else-if="this.card.vendor === 'Evil-corp'" class="vendor-logo" src="../assets/vendor-evil.svg" alt="logo" />
       
        <p class="card-number">{{ cardNumber }}</p>
        <p class="p-name">CARDHOLDER NAME</p>
        <p class="card-name">{{ cardHolder }}</p>
        <p class="p-valid">VALID THRU</p>
        <p class="card-valid">{{ cardVaildDate }}</p>
     
    
  </div>

</div>
  
</template>

<script>
export default {

    props: {

        card: Object

    },

    computed: {

        cardNumber() {

            return   `
                    ${this.card.number.slice(0, 4)}
                    ${this.card.number.slice(4, 8)}
                    ${this.card.number.slice(8, 12)}
                    ${this.card.number.slice(12, 16)}
                     `
        },

        cardHolder() {

            return this.card.name
        },

        cardVaildDate() {

            return `${this.card.month} / ${this.card.year}`
        },

        cardColor() {

            if(this.card.vendor === 'bitcoin-inc') {

                return 'c-bitcoin'

            }
            else if(this.card.vendor === 'Ninja-bank') {

                return 'c-ninja'

            }
            else if(this.card.vendor === 'Block-chain-INC') {

                return 'c-block'

            }
            else if(this.card.vendor === 'Evil-corp') {

                return 'c-evil'

            }
            else {

                return 'c-gray'

            }
        },   
    }  
}

</script>

<style lang="scss" scoped>

.card-wrapper {
    display: flex;
    justify-content: center;
}

.card {
    width: 40rem;
    height: 250px;
    border-radius: 10px;
    box-shadow: 7px 7px 5px rgb(160, 157, 157);
    display: grid;
    grid-template-rows:100px 65px 20px 65px;
    grid-template-columns:2fr 1fr;
    cursor: pointer;
}

.vendor-chip {
    grid-row: 1/2;
    grid-column: 1/2;
    padding-left: 20px;
    padding-top: 20px;
}

.vendor-logo {
    grid-row: 1/2;
    grid-column: 2/3;
    padding-top: 30px;
    padding-left: 50px;
}

.card-number {
    grid-row: 2/3;
    grid-column: 1/3;
    font-size: 3rem;
    transform: scale(1.2, 1);
}

.p-name {
    grid-row: 3/4;
    grid-column: 1/2;
    font-size: 0.8rem;
    padding-left: 20px;
    text-align: left;
    margin-top: 25px;
}

.p-valid {
    grid-row: 3/4;
    grid-column: 2/3;
    font-size: 0.8rem;
    margin-top: 25px;
    text-align: left;
}

.card-name{
    grid-row: 4/5;
    grid-column: 1/2;
    font-size: 2rem;
    text-align: left;
    padding-left: 20px;    
}

.card-valid {
    grid-row: 4/5;
    grid-column: 2/3;
    font-size: 2rem;
    text-align: left;
}


.c-bitcoin {
  background-color: rgb(245, 171, 33);
}

.c-ninja {
    color: white;
    background-color: rgb(56, 54, 54);
}

.c-block {
    color: white;
    background-color: rgb(153, 116, 177);
    text-shadow: 1px 2px 5px rgb(43, 41, 41);
}

.c-evil {
    color: white;
    background-color: rgb(179, 44, 84);
    text-shadow: 1px 2px 5px rgb(43, 41, 41);
}

.c-gray {
    background-color: rgb(212, 207, 207);
}


</style>