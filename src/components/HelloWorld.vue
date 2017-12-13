<template>
  <div class="hello" style="max-width:200px;">
    {{user.username}}
    {{user.feedback_positive}}
  
  </div>
</template>

<script>
import CryptoJS from 'crypto-js'
import axios from 'axios'
import qs from 'qs'
import Vue from 'vue';
export default {
  name: 'HelloWorld',
  data() {
    return {
      user:{
        username:'',
        feedback_positive:''
      },
    };
  },
  watch: {
    text() {
      console.log('object');
    }
  },
  mounted() {
    var xhr = new XMLHttpRequest()
    const	secret = 'civQx4YDhsO6nmQ0yvlfQmByanitrVB6'
    const key = 'zNHUeqIzWoBY26HKpaKdIfb8tJD5bPaw'
    const body = 'apikey=' + key + '&nonce=' + Date.now() + '&username=RTSullivan';
      
    var seal = CryptoJS.HmacSHA256(body, secret);
    // var url = body + '&apiseal=' + seal;
    // xhr.open('POST', 'https://paxful.com/api/user/info');
    // xhr.setRequestHeader('Content-Type', 'text/plain');
    // xhr.setRequestHeader('Accept', 'application/json');
    // xhr.send(url);
    // console.log(url);
    // xhr.onreadystatechange = () => {
    //   if(xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    //       const info = JSON.parse(xhr.responseText).data
    //       this.user.username = info.username
    //       this.user.feedback_positive = info.feedback_positive
    //   }
    // }
   const url = 'https://paxful.com/api/user/info';
  // The data we are going to send in our request
  const dataTemp = qs.stringify({'apikey': key, 'nonce' : Date.now(), 'username' : 'RTSullivan'})
  const data = dataTemp + '&apiseal=' + seal
  

  // The parameters we are gonna pass to the fetch function
  let fetchData = { 
      method: 'POST', 
      body: data,
      headers: new Headers()
  }
  fetch(url, fetchData)
  .then(data => {
    console.log(data);
  });
      // apikey=zNHUeqIzWoBY26HKpaKdIfb8tJD5bPaw&nonce=1512710904319&username=RTSullivan&apiseal=02deeea540f84d34befb0bc079044512259e9fb513a058a91b94d18ced7f0dd1
    // apikey=zNHUeqIzWoBY26HKpaKdIfb8tJD5bPaw&nonce=1512710904327&username=RTSullivan&apiseal=02deeea540f84d34befb0bc079044512259e9fb513a058a91b94d18ced7f0dd1
    // const data = qs.stringify({'apikey': key, 'nonce' : Date.now(), 'username' : 'RTSullivan'})
    // // console.log(qs.stringify({'apiseal': seal}));
    // const dataaa = data + '&apiseal=' + seal
    // console.warn(dataaa);
    // const config = {
    //   headers: {
    //     'Content-Type' : 'text/plain',
    //     'Accept' : 'application/json'
    //   }
    // }
    // axios.post('https://paxful.com/api/user/info', dataaa, config)
    // .then(data => {
    //   console.error(data);
    // })
    // xhr.open('POST', 'https://paxful.com/api/wallet/balance');
    // xhr.setRequestHeader('Content-Type', 'text/plain');
    // xhr.setRequestHeader('Accept', 'application/json');
    // xhr.send(url);
    // xhr.onreadystatechange = () => {
    //   if(xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    //       const info = JSON.parse(xhr.responseText).data
    //       console.log(info);
    //       //1 satoshi = 0.00000001 BTC
    //   }
    // }
    // xhr.open('POST', 'https://paxful.com/api/transactions/all');
    // xhr.setRequestHeader('Content-Type', 'text/plain');
    // xhr.setRequestHeader('Accept', 'application/json');
    // xhr.send(url);
    // xhr.onreadystatechange = () => {
    //   if(xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    //       const info = JSON.parse(xhr.responseText).data.transactions
    //       console.log(info);
    //   }
    // }
    // xhr.open('POST', 'https://paxful.com/api/currency/rates');
    // xhr.setRequestHeader('Content-Type', 'text/plain');
    // xhr.setRequestHeader('Accept', 'application/json');
    // xhr.send(url);
    // xhr.onreadystatechange = () => {
    //   if(xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    //       const info = JSON.parse(xhr.responseText).data
    //       console.log(info);
    //       //all currency rates
    //   }
    // }
    // xhr.open('POST', 'https://paxful.com/api/currency/btc');
    // xhr.setRequestHeader('Content-Type', 'text/plain');
    // xhr.setRequestHeader('Accept', 'application/json');
    // xhr.send(url);
    // xhr.onreadystatechange = () => {
    //   if(xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    //       const info = JSON.parse(xhr.responseText)
    //       console.log(info);
    //       //BTC => USD
    //   }
    // }
    // xhr.open('POST', 'https://paxful.com/api/currency/btc');
    // xhr.setRequestHeader('Content-Type', 'text/plain');
    // xhr.setRequestHeader('Accept', 'application/json');
    // xhr.send(url);
    // xhr.onreadystatechange = () => {
    //   if(xhr.readyState == XMLHttpRequest.DONE && xhr.status == 200) {
    //       const info = JSON.parse(xhr.responseText)
    //       console.log(info);
    //       //BTC => USD
    //   }
    // }
  }
};
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
