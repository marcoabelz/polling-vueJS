<template>
  <div class="container">
  	<section class="vote">
  		<h3 class="give-your-vote">
  			Silahkan berikan penialaian anda terhadap pelayanan kami.
  		</h3>

  		<div class="emoticons">
  			ini akan menjadi komponen vote
  		</div>
  	</section>

  	<section class="finish">
  		
  		<h4>Terima kasih telah memberikan penilaian anda</h4>

  	</section>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {}
};
</script>
<style type="text/css">
	.container{
		display: flex;
		height: 100vh;
		flex-wrap: wrap;
		align-items: center;
	}
	section{
		width: 100%;
	}
</style>