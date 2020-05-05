<template>
  <div class="buttons">
    <!-- v-for untuk melakukan looping di dalam vue, emoticon, index akan mendapatkan nilai dari arrary emoticons. key mendapatkan nilai dari index,
    id akan mendapatkan nilai perulangan dari emoticon || value agar semua emoticon memiliki valuenya masing2 || vote adalah nama method (29) -->
    <button v-for="(emoticon, index) in emoticons" 
            :key="index"
            :id="emoticon"
            :value="emoticon" 
            @click="vote"
            class="btn-emoticon"
    ></button>

  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";
import moment from "moment";

export default {
  name: "Home",
  components: {},
  data: function(){
    return {
      emoticons: ['very-bad','bad','ok','good','very-good'] //membuat array emoticons
    }
  },
  methods:{
    vote(e){ //e adalah event || console.log(e); -> hapus baris 30 32 ganti baris 31 , -> inspect -> console -> target -> value
      var voted = e.target.value;
      //console.log(voted);
      var keyStorage = moment().format('YYYYMMDDhhmmss'); //digunakan sebagai key dinamis untuk menyimpan data dengan value yg berbeda (gantinya id)
      var created_at = moment().format('YYYY-MM-DD, hh:mm:ss');
      
      var data = {
        vote: voted,
        created_at: created_at
      }

      //console.log(data);

      var jsonToString = JSON.stringify(data); //JSON.stringify(data) mengubah isi variabel data dari JSON menjadi string agar bisa di save di local storage

      //console.log(jsonToString);

      localStorage.setItem(keyStorage, jsonToString); //menyimpan nilai voted ke dalam nilai kunci vote di dalam local storage (inpect -> application -> localstorage)
    }
   }
  };
</script>

<style type="text/css">
  .emoticons {
    justify-content: center;
    display: flex;
  }

  .buttons{
    display: flex;
  }

  .btn-emoticon{
    background: url('../assets/emot-active.png');
    width: 88px;
    height: 100px;
    border: none;
    margin: 0px 15px;
    cursor: pointer;
    outline: none;
    align-items: center;
  }

  #very-bad{
    background-position: -413.2px 0px;
  }
  #very-bad:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -413.2px 0px;
  }
  #very-bad:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -413.2px 0px;
    border-style: inset;
  }

  #bad{
    background-position: -311px 0px;
  }
  #bad:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -311px 0px;
  }
  #bad:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -311px 0px;
    border-style: inset;
  }

  #ok{
    background-position: -208px 0px;
  }
  #ok:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -208px 0px;
  }
  #ok:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -208px 0px;
    border-style: inset;
  }

  #good{
    background-position: -105px 0px;
  }
  #good:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -105px 0px;
  }
  #good:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -105px 0px;
    border-style: inset;
  }
  #very-good{
    background-position: 0.2px 0px;
  }
  #very-good:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: 0.2px 0px;
  }
  #very-good:active{
    background: url('../assets/emot-active-klik.png');
    background-position: 0.2px 0px;
    border-style: inset;
  }




</style>