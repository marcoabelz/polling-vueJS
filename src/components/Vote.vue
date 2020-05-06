<template>
  <div>
    <section class="button-emot">
      <div class="buttons">
        <!-- v-for untuk melakukan looping di dalam vue, emoticon, index akan mendapatkan nilai dari arrary emoticons. key mendapatkan nilai dari index,
        id akan mendapatkan nilai perulangan dari emoticon || value agar semua emoticon memiliki valuenya masing2 || vote adalah nama method (47) || :class = jika nilai emoticon hasil looping memiliki nilai yang sama dengan emoticon yg sedang di klik, maka emoticon tsb
        akan di tambahkan kelas active line 53-->
        <button v-for="(emoticon, index) in emoticons" 
                :key="index"
                :id="emoticon"
                :value="emoticon" 
                @click="vote"
                :class="{active: emoticon == emoticonClick}"
                :disabled="isDisable" 
                class="btn-emoticon">
      </button>
      </div>
    </section>
    <section class="penjelasan-emot">        
      <div class="very-bad">Very Bad</div>
      <div class="bad">Bad</div>
      <div class="ok">Ok</div>
      <div class="good">Good</div>
      <div class="very-good">Very Good</div>
    </section>
      <!--v-for="(emoticon) in emoticons" 
             class="penjelasan-emot">
      <div v-if="emoticon === 'very-bad'" >Very Bad</div>
      <div v-else-if="emoticon === 'bad'" >Bad</div>
      <div v-else-if="emoticon === 'ok'" >Ok</div>
      <div v-else-if="emoticon === 'good'" >Good</div>
      <div v-if="emoticon === 'very-good'" >Very Good</div>
    </section>-->
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";
import moment from "moment";

export default {
  name: "Vote",
  props: {
    voteProp : { //Home.vue line 9
      type : Function //type voteProp = function
    }
  },
  data: function(){
    return {
      emoticons: ['very-bad','bad','ok','good','very-good'], //membuat array emoticons
      //isDisable: false,
      emoticonClick: '' //jika nilai true maka kelas active akan ditambahkan pada button, kalo false nilainya akan dihapus
    }
  },
  methods:{
    vote(e){ //e adalah event || console.log(e); -> hapus baris 30 32 ganti baris 31 , -> inspect -> console -> target -> value
      var voted = e.target.value;
      //this.isDisable=true; //ketika isDisable bernilai true, maka button emot tidak bisa di klik lagi
      this.emoticonClick= voted; //emoticonClick akan diisi berdasarkan value icon yg di klik
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

      this.voteProp();
    }
   },
   computed:{
    isDisable : function(){
      return this.emoticonClick.length === 0 ? false : true; //jika nilai string di dalam emoticionClick 0 maka nilainya false, jika >0 maka true
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
    background-position: -412px 0px;
  }
  #very-bad:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -412px 0px;
  }
  #very-bad.active,
  #very-bad:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -412px 0px;
    /*border-style: inset;*/
    
  }

  #bad{
    background-position: -311px 0px;
  }
  #bad:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -311px 0px;
  }
  #bad.active,
  #bad:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -311px 0px;
    /*border-style: inset;*/
  }

  #ok{
    background-position: -208px 0px;
  }
  #ok:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -208px 0px;
  }
  #ok.active,
  #ok:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -208px 0px;
    /*border-style: inset;*/
  }

  #good{
    background-position: -105px 0px;
  }
  #good:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: -105px 0px;
  }
  #good.active,
  #good:active{
    background: url('../assets/emot-active-klik.png');
    background-position: -105px 0px;
    /*border-style: inset;*/
  }
  #very-good{
    background-position: 0.2px 0px;
  }
  #very-good:hover{
    background: url('../assets/emot-active-klik.png');
    background-position: 0.2px 0px;
  }
  #very-good.active,
  #very-good:active{
    background: url('../assets/emot-active-klik.png');
    background-position: 0.2px 0px;
    /*border-style: inset;*/
  }




  section.penjelasan-emot {
    display: flex;
    width: 600px;
    padding-top: 10px;

    }

    .very-bad {
       padding-left: 26px;
    }

    .bad {
       padding-left: 70px;
    }

    .ok {
      padding-left: 93px;
    }

    .good {
      padding-left: 88px;
    }

    .very-good {
      padding-left: 65px;
    }



</style>