<template>
  <div class="top">

    <div id="nav">
      <router-link to="/">BACK TO HOME</router-link> 
    </div>

    <AppTop 
      :title="addCardTitle"
      :cardTitle="addCardCardTitle"/>

     
    <SingleCard :card="newCard"/>

    <CardForm @addCardNumber="addCardNumber"
              @addCardHolderName="addCardHolderName"
              @addVaildMonth="addVaildMonth"
              @addVaildYear="addVaildYear"
              @addCardVender="addCardVender"/>

    <p v-if="errors.length">
      <b>Please correct the following error(s):</b>
        <ul>
            <li v-for="error in errors" :key="error.index">
               {{ error }}
            </li>
        </ul>
    </p>

    <button class="add-button" @click="checkAndAdd">ADD CARD</button>

  </div>

</template>

<script>

import AppTop from '../components/AppTop.vue'
import CardForm from '../components/CardForm.vue'
import SingleCard from '../components/SingleCard.vue'


export default {

  components: {

    AppTop,
    CardForm,
    SingleCard

  },

  data() {

    return {

      addCardTitle: 'ADD A NEW BANK CARD',
      addCardCardTitle: 'NEW CARD',
      
      newCard: {
                number: 'XXXX XXXX XXXX XXXX',
                name: 'FIRSTNAME LASTNAME',
                month: 'MM',
                year: 'YY',
                vendor: ''
            },

        errors: [],
    }
  },

  methods: {

    addCardNumber(number) {

      this.newCard.number = number
    },

    addCardHolderName(name) {

      this.newCard.name = name
    },

    addVaildMonth(month) {

      this.newCard.month = month
    },

    addVaildYear(year) {

      this.newCard.year = year
    },

    addCardVender(vendor) {

      this.newCard.vendor = vendor
    },


    checkAndAdd() {
       
      let flag = 0
      this.errors = []

      if(this.newCard.number.length < 16) {

        flag = 1 
        this.errors.push('Please input 16 digits')

      }
      else if(!this.newCard.number.match(/^[0-9]+$/)){

        flag = 1
        this.errors.push('Please input numbers')

      }
      else if(this.newCard.name == 'FIRSTNAME LASTNAME'){

        flag = 1
        this.errors.push('Please input a cardholder name')

      }
      else if(this.newCard.name.length < 2){

        flag = 1
        this.errors.push('Cardholder\'s name must be at least 2 characters')

      }
      else if(this.newCard.name.match(/^[0-9]+$/)) {

        flag = 1
        this.errors.push('Cardholder\'s name must be letters')

      }
      else if(this.newCard.month == 'MM') {

        flag = 1
        this.errors.push('Please select a month')

      }
      else if(this.newCard.year == 'YY') {

        flag = 1
        this.errors.push('Please select a year')

      }
      else if(this.newCard.vendor == '') {

        flag = 1
        this.errors.push('Please select a vendor')

      }
      
      if(flag) {

        return 

      } else { 

        this.addNewCard()
      }

    },

  
    addNewCard() {

      if(this.$root.$data.cards.length >= 1){
        let id = this.$root.$data.cards.map(function (c) {
        return c.id;
        });
          let maxIdNumber = Math.max.apply(null, id)
          this.newCard.id = maxIdNumber +1
      }
      else{

        this.newCard.id = 1
      }
      
      this.$root.$data.cards.push(this.newCard)
      this.$router.push("/")
    },
  }
    

}



</script>

<style lang="scss" scoped>



#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}

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

p {
  font-size: 1.5rem;
  color: rgb(241, 13, 13);
}


</style>