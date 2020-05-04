<template>
  <div class="buttons">
    <!-- v-for untuk melakukan looping di dalam vue, emoticon, index akan mendapatkan nilai dari arrary emoticons. key mendapatkan nilai dari index,
    id akan mendapatkan nilai perulangan dari emoticon -->
    <button v-for="(emoticon, index) in emoticons" 
            :key="index"
            :id="emoticon"
            class="btn-emoticon"
    ></button>

  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {},
  data: function(){
    return {
      emoticons: ['very-bad','bad','ok','good','very-good'] //membuat array emoticons
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