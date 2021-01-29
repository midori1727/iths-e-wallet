<template>
  <div class="card-form-wrapper">

      <form>
          <section>
              <label for="card-number">CARD NUMBER</label>
                <input type="text"
                 name="card-number"
                 placeholder=" XXXX XXXX XXXX XXXX"
                 maxlength="16"
                 v-model="formData.cardNumber"
                 @input="addCardNumber"
                 required>
          </section>

          <section>
              <label for="cardholder-name">CARDHOLDER NAME</label>
              <input type="text"
                 name="cardholder-name"
                 placeholder="FIRSTNAME LASTNAME"
                 maxlength="23"
                 v-model="formData.cardHolderName"
                 @input="addCardHolderName"
                 required>
          </section>

          <section>
              <label for="valid-month">VALID MONTH</label>
              <select name="month" v-model="formData.vaildMonth" @change="addVaildMonth">
                <option value="1">01</option>
                <option value="2">02</option>
                <option value="3">03</option>
                <option value="4">04</option>
                <option value="5">05</option>
                <option value="6">06</option>
                <option value="7">07</option>
                <option value="8">08</option>
                <option value="9">09</option>
                <option value="10">10</option>
                <option value="11">11</option>
                <option value="12">12</option>
            </select>
          </section>

          <section>
              <label for="valid-year">VALID YEAR</label>
              <select name="year" v-model="formData.vaildyear" @change="addVaildYear">
                <option value="21">21</option>
                <option value="22">22</option>
                <option value="23">23</option>
                <option value="24">24</option>
                <option value="25">25</option>
                <option value="26">26</option>
              </select>
          </section>

          <section>

              <label for="Vendor">VENDOR</label>
              <select name="Vendor" v-model="formData.cardVendor" @change="addCardVender">
                <option value="bitcoin-inc">bitcoin inc</option>
                <option value="Ninja-bank">Ninja Bank</option>
                <option value="Block-chain-INC">Block chain INC</option>
                <option value="Evil-corp">Evil corp</option>
              </select>
          </section>

      </form>

  </div>
</template>

<script>


export default {

    data() {
        
        return {

            formData: {
                
                id: '',
                cardNumber: '',
                cardHolderName: '',
                vaildMonth: '',
                vaildyear: '',
                cardVendor: ''
            },
        }
    },

    methods: {

        addCardNumber() {

            this.$emit('addCardNumber', this.formData.cardNumber)
            
        },

        addCardHolderName() {

            this.$emit('addCardHolderName', this.formData.cardHolderName)
        },

        addVaildMonth() {

            this.$emit('addVaildMonth', this.formData.vaildMonth)
        },

        addVaildYear() {

            this.$emit('addVaildYear', this.formData.vaildyear)
        },

        addCardVender() {

            this.$emit('addCardVender', this.formData.cardVendor)
        },


    }
}
</script>

<style lang="scss" scoped>


form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 4rem;
    margin-bottom: 4rem;
}

label {
    text-align: left;
    margin-top: 0.5rem;
    margin-bottom: 0.5rem;
    font-size: 1.5rem;
    display: block;
}

input {
    width: 35rem;
    text-align: center;
    padding: 1rem 1.5rem;
    border-radius: 10px;
    border: 2px solid rgb(155, 149, 149);
}

select {
    width: 38rem;
    text-align: center;
    padding: 1rem 1.5rem;
    border-radius: 10px;
    border: 2px solid rgb(155, 149, 149);
}

input:focus, select:focus {
    box-shadow: 0 0 5px 0 rgba(255,153,0,1);
    border: 2px solid #FFF !important;
    outline: 0;
}

</style> 