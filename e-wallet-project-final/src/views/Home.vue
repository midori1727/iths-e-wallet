<template>
  <div class="home">
    <AppTop :title="homeTitle"
            :cardTitle="homeCardTitle"/>

    <SingleCard v-if="this.$root.$data.cards.length > 0" :card="activeCard"
                @click.native="removeAktiveCard"/>

    <p v-show="this.$root.$data.cards.length > 1">CARD STACK</p>
    
    <CardStack/>

    <div id="button">
      <button @click="addCard" class="add-button">ADD A NEW CARD</button>
    </div>  
  </div>
</template>

<script>

import AppTop from '../components/AppTop.vue'
import SingleCard from '../components/SingleCard.vue'
import CardStack from '../components/CardStack.vue'


export default {
  name: "Home",
  components: {

    AppTop,
    SingleCard,
    CardStack
  },

  data() {
    
    return {

      homeTitle: 'E-WALLET',
    }
  },

  computed: {

     homeCardTitle() {

      if(this.$root.$data.cards.length < 1){

        return 
      }
      else {

        return 'ACTIVE CARD'
      }
     },

    activeCard() {

        return this.$root.$data.cards[this.$root.$data.activeCardIndex]
    }
  },

  methods: {

    removeAktiveCard() {

      let result = confirm('Do you want to remove the aktive card?')

      if(result) {

        return this.$root.$data.cards.splice(0,1)
      }
      else {

        return false
      }
   },

    addCard() {

      this.$router.push("/addCard")
   }
  }
};


</script>

<style lang="scss" scoped>

#button {
  display: flex;
  justify-content: center;

  .add-button {
    font-size:2rem;
    color: black;
    width:40rem;
    padding-top:1rem;
    padding-bottom:1rem;
    text-align:center;
    border:2px solid;
    border-color:#aaaaaa #444444 #444444 #aaaaaa;
  }

  .add-button:hover {
    background-color: black;
    color: white;
  }
}

p {
  font-size: 1.3rem;
  color: rgb(173, 170, 170);
  margin-top: 3rem
}



</style>
