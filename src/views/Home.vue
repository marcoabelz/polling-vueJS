<template>
  <div class="container">
  	<section class="vote">
  		<h3 class="give-your-vote">
  			Silahkan berikan penialaian anda terhadap pelayanan kami.
  		</h3>

  		<div class="emoticons">
  			<vote :voteProp="vote"/> <!--voteProp akan dikirim ke dalam vote componen, setelah mendapat hasil dari vote komponen maka method di dalam voteProp,
  			 (vote) akan dijalankan (37) -->
  		</div>
  	</section>

  	<section class="finish">

  		<transition name="fade">
  		
  			<h4 v-if="show">Terima kasih telah memberikan penilaian anda</h4> <!-- v-if="show" untuk menghilangkan tulisan terima kasih-->

  		</transition>
  	</section>
  </div>
</template>

<script>
// @ is an alias to /src
import Vote from "@/components/Vote.vue";

export default {
  name: "Home",
  data: function(){
  	return{
  		show: false //membuat data show dari line 17, false = hilang, true = ada
  	}
  },
  components: { Vote },
  methods: {
  	vote(){
  		this.show = true;
  	}
  }
};
</script>
<style type="text/css">

	.fade-enter-active, .fade-leave-active {
		transition: opacity 1s;
	}
	.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
		opacity: 0;
	}

	.give-your-vote{
		font-size: 20px;
	}

	.emoticons {
	    justify-content: center;
	    display: flex;
	  }
	.container{
		display: flex;
		height: 100vh;
		flex-wrap: wrap;
		align-items: center;
	}

	section{
		width: 100%;
	}

	.finish{
		position: absolute;
		bottom: 20px;
	}

</style>