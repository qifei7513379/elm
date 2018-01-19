<template>
	<div class="header">
		<div class="content-wrapper">
			<div class="avatar">
				<img width="64" height="64" :src="seller.avatar"/>
			</div>
			<div class="content">
				<div class="title">
					<span class="brand"></span>
					<span class="name">{{seller.name}}</span>
				</div>
				<div class="description">
					{{seller.description}}/{{seller.deliveryTime}}分钟送达
				</div>
				<div class="support" v-if="seller.supports">
					<span class="icon" :class="classMap[seller.supports[0].type]"></span>
					<span class="text">{{seller.supports[0].description}}</span>
				</div>
			</div>
			<div class="support-count" v-if="seller.supports" v-on:click="clickCount">
				{{seller.supports.length}}个    ›
			</div>
		</div>
		<div class="bulletin-wrapper" @click="clickCount">
			<div class="bulletin-icon">
				
			</div><div class="bulletin-title">
				{{seller.bulletin}}
			</div><div class="bulletin-click"> › </div>
		</div>
		<div class="bg">
			<img :src="seller.avatar"/>
		</div>
		<transition name="fade">
		    <div class="detail" v-if="show">
				<div class="close" @click="close">
					×
				</div>
			</div>
		</transition>
		
	</div>
	
</template>

<script>
	export default{
		props:{
			seller:{
				type:Object
			}
		},
		created(){
			this.classMap = ["decrease","discount","special","invoice","guarantee"];
		},
		methods:{
			clickCount:function(event){
				this.show = true				
			},
			close:function(event){
				this.show = false	
			}
		},
		data () {
	    return {
	      show:false,
	    }
	 }
	};
</script>

<style>
	.header{color: white;background: rgba(7,17,27,.5);position: relative;overflow: hidden;}
	.content-wrapper{padding: 24px 18px 12px 24px;font-size: 0;position: relative;}
	.avatar{display: inline-block;vertical-align: top;}
	.content{display: inline-block;margin-left: 16px;}
	.title{margin: 2px 0 8px 0;}
	.description{font-size: 12px;margin: 8px 0 10px 0;font-weight: 200;line-height: 12px;}
	.support{}
	.brand{width: 30px;height: 18px;display: inline-block;background: url(brand@3x.png) no-repeat;background-size: 30px 18px;vertical-align: top;}
	.name{font-size: 16px;margin-left: 6px;line-height: 18px;font-weight: bold;}
	.text{font-size: 10px;font-weight: 200;line-height: 12px;}
	.avatar img{border-radius: 2px;}
	.icon {display: inline-block;width: 12px;height: 12px;margin-right: 4px;vertical-align: top;}
	.decrease{background: url(decrease_1@3x.png) no-repeat;background-size: 12px 12px;}
	.discount{background: url(discount_1@3x.png) no-repeat;background-size: 12px 12px;}
	.invoice{background: url(invoice_1@3x.png) no-repeat;background-size: 12px 12px;}
	.special{background: url(special_1@3x.png) no-repeat;background-size: 12px 12px;}
	.guarantee{background: url(guarantee_1@3x.png) no-repeat;background-size: 12px 12px;}
	.support-count{color: white;position: absolute;right: 12px;bottom: 10px;font-size: 12px;padding: 7px 8px;background: rgba(0,0,0,.2);border-radius: 24px;line-height: 12px;}
	.bulletin-wrapper{height: 28px;background: rgba(7,17,27,.2);line-height: 28px;padding:0 22px 0 12px;text-overflow: ellipsis;white-space: nowrap;overflow: hidden;position: relative;}
	.bulletin-title{display: inline;font-size: 10px;margin-left: 4px;vertical-align: top;}
	.bulletin-icon{background: url(bulletin@3x.png) no-repeat;background-size: 22px 12px;width: 22px;height: 12px;display: inline-block;width: 22px;}
	.bulletin-click{display: inline-block;font-size: 12px;width: 10px;position: absolute;right: 12px;}
	.bg{position: absolute;top: 0;left: 0;z-index: -1;width: 100%;overflow: hidden;filter: blur(10px);}
	.bg img{width: 100%;}
	
	/*弹窗*/
	.detail{position: fixed;min-height: 100%;background: rgba(7,17,27,.8);top: 0;width: 100%;}
	.fade-enter-active, .fade-leave-active {
	  transition: opacity .5s;
	}
	.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
	  opacity: 0;
	}
</style>