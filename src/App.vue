<template>
  <div id="app">
  	<headerNav></headerNav>
  	<div class="tab">
  		<div class="tab-item">
  			<router-link to="/">商品</router-link>
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
	import headerNav from '@/components/header/header.vue'
	
	export default {
		components: { headerNav }
	}
</script>

<style>
	
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.tab {width: 100%;display: flex;height: 40px;line-height: 40px;}
.tab-item{flex: 1;}
</style>
