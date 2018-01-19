<template>
  <div id="app">
  	<v_header :seller="seller"></v_header>
  	<div class="tab">
  		<div class="tab-item">
  			<router-link to="/goods">商品</router-link>
  		</div>
  		<div class="tab-item">
  			<router-link to="/ratings">评论</router-link>
  		</div>
  		<div class="tab-item">
  			<router-link to="/seller">商家</router-link>
  		</div>
  	</div>

    <router-view/>
  </div>
</template>

<script>
	import v_header from '@/components/header/header.vue'
	
	export default {
		data () {
	    return {
	      seller:{}
	    }
	 },
	 	created () {
	 		  // GET /someUrl
		  this.$http.get('http://localhost:3000/seller').then(response => {
				
		    // get body data
		    this.someData = response.body;
			if(this.someData.errno == 0){
				this.seller = response.body.data;
				console.log(this.seller)
			}
				
		  }, response => {
		    // error callback
		  });
	 	},
		components: { v_header }
	}
</script>

<style>

.tab {width: 100%;display: flex;height: 40px;line-height: 40px;border-bottom: 0.5px solid rgba(7,17,27,.1);}
.tab-item{flex: 1;font-size: 14px;color: rgb(77,85,93);line-height: 40px;text-align: center;}
.tab-item>a{display: block;height: 100%;}
.router-link-active{color: rgb(240,20,20);}
</style>
