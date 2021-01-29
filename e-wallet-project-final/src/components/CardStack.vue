<template>
    <div class="card-stack">
        <SingleCard  v-for="(card, index) in cardStack"
                     :key="index"
                     :card="card"
                     @click.native="changeAndRemove(card)"
                     :style="{ zIndex: index }"/>
    </div>
</template>

<script>

import SingleCard from './SingleCard.vue'

export default {

    components: {

        SingleCard
    },

    computed: {

    activeCard() {
      return this.$root.$data.cards[this.$root.$data.activeCardIndex]
      
    },

    cards() {

        return this.$root.$data.cards
    },

    cardStack() {

        let cardStack = this.$root.$data.cards.filter(function(value,index) {
            return index > 0
        })

        return cardStack
    }
  },

  
    methods: {

        removeCard(card) {

            let result = confirm('Do you want to remove this card?')
            
            if(result) {

                let index = this.cards.indexOf(card)
                this.cards.splice(index, 1)
            } 
            else {

                return false
            }
        },

        changeAndRemove(card) {

            let result = confirm('Do you want this card as an aktive card?')
            
            if(result) {

                let index = this.cards.indexOf(card)
                this.$root.$data.cards.unshift(card) 
                this.cards.splice(index+1, 1)
            } 

            else {

                this.removeCard(card)
            }
            },   
    }
}
</script>

<style lang="scss" scoped>

.card-stack {
  margin: 2rem 0 25rem;
  display: grid;
  grid-auto-rows: 5rem;
}


</style>