<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Benjarat" />
    <button-icon @buttonText="popup"></button-icon>
    <br />
    <button-icon icon="fa fa-users" name="User"></button-icon> -->
    <navbar></navbar>
    <div class="container">
      <button class="btn btn-success" @click="isNew = !isNew">Create</button>
      <div class="form-group row"></div>
      <receipt-form v-if="isNew" @saveReceipt="addReceipt"></receipt-form>
      <input type="text" class="form-control" v-model="searchtext">
      <ul>
        <li v-for="(receipt,index) in filterList" :key="index+receipt.title">{{receipt.title}}</li>
        <!-- <li v-for="(receipt,index) in receipts" :key="index+receipt.title">{{receipt.title}}</li> -->
        <!-- <li v-for="(receipt,index) in receipts" :key="index+receipt.imgurl">{{receipt.imgurl}}</li>
        <li v-for="(receipt,index) in receipts" :key="index+receipt.description">{{receipt.description}}</li>
        <li v-for="(receipt,index) in receipts" :key="index+receipt.ingredient['']">{{receipt.ingredient['']}}</li> -->
      </ul>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
// import ButtonIcon from './components/ButtonIcon.vue';
import navbar from './layouts/navbar.vue';
import ReceiptForm from './components/ReceiptForm.vue';

export default {
  name: 'app',
  components: {
    // HelloWorld, ButtonIcon
    navbar, ReceiptForm
  },
  data () {
    return {
      receipts: [],
      isNew: false,
      searchtext: ''
    }
  },
  mounted () {
    if (localStorage.getItem('receipts')) {
      this.receipts = JSON.parse(localStorage.getItem('receipts'))
    }
  },
  computed: {
     filterList() {
      return this.receipts.filter(receipt => {
        return receipt.title.toLowerCase().indexOf(this.searchtext.toLowerCase()) > -1
      })
    }
  },
  methods: {
    // popup (text) {
    //   alert(text)
    // },
    setLocalStorage () {
      localStorage.setItem('receipts', JSON.stringify(this.receipts))
    },
    addReceipt (receipt) {
      this.receipts.push(receipt)
      this.setLocalStorage()
      this.isNew = false;
      //console.log(receipt)
      // alert(receipt)
    },
    // searchReceipt () {
    //   this.receipts = this.receipts.filter((receipt) => {
    //     return receipt.title.toLowerCase().indexof(this.searchtext.toLowerCase()) > -1
    //   })
    //   // this.receipts = this.receipts.filter((value) => {
    //   //   return value === this.searchtext
    //   // })
    //   // console.log(this.searchtext)
    // }
  },
}
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>
