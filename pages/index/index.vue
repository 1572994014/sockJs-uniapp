<template>
	<view>
		<text>{{text}}</text>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text: ''
			}
		},
		onLoad() {
			// 连接地址在local.html中填写
			let that = this
			//#ifdef APP-PLUS
			let wv =  plus.webview.create("/hybrid/html/local.html")
			plus.globalEvent.addEventListener('plusMessage', function(msg){  
				if(msg.data.args.data.name == 'postMessage'){   
					that.text = msg.data.args.data.arg.message.body
					plus.push.createMessage("测试消息", that.text, {})

				}  
			});
			//#endif
		},
		methods: {

		}
	}
</script>

<style>
</style>
