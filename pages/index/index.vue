<template>
	<view>
		<status-bar @statusEvent='statusEvent' :fontItems='frontStatusItems' :backItems='backStatusItems' :hasContent='true' :hasPlaceholder='true'></status-bar>
		<basics v-if="PageCur == 'basics'"></basics>
		<components v-if="PageCur == 'component'"></components>
		<plugin v-if="PageCur == 'plugin'"></plugin>
		<nav-bar @navChange='navChange' :items='navItems' ></nav-bar>
	</view>
</template>

<script>
import navBar from '@/components/nav-bar.vue';
export default {
	components: {
		navBar
	},
	data() {
		return {
			PageCur: 'basics',
			navItems: [
				{title: "元素", cur: "basics"},
				{title: "组件", cur: "component"},
				{title: "扩展", cur: "plugin"}
			],
			frontStatusItems: [
				{title: "用户", cur: "user", icon: "\ue736"}
			],
			backStatusItems: [
				// {title: "扫码", cur: "scan", icon: "\ue689"},
				// {title: "拍摄", cur: "photo", icon: "\ue665"}
			]
		};
	},
	methods: {
		navChange: function(cur) {
			this.PageCur = cur;
			console.log(this.PageCur)
		},
		statusEvent: function(cur){
			console.log(cur)
		}
	}
};
</script>

<style></style>
