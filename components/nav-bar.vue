<template>
	<view class="cu-bar tabbar bg-white shadow foot">
		<view v-for="(item, index) in items" class="action" @click="navChange" :data-cur="item.cur" :key="index">
			<view class="cuIcon-cu-image"><image :src="'/static/tabbar/' + item.cur + [PageCur == item.cur ? '_cur' : ''] + '.png'"></image></view>
			<view :class="PageCur == item.cur ? 'nav-action' : 'nav-default'">{{ item.title }}</view>
		</view>
	</view>
</template>

<script>
export default {
	name: 'nav-bar',
	data() {
		return {
			PageCur: 'basics'
		};
	},
	onLoad() {
	},
	methods: {
		navChange: function(e) {
			this.PageCur = e.currentTarget.dataset.cur;
			this.$emit('navChange', this.PageCur);
		}
	},
	props: {
		items: Array,
	}
};
</script>

<style>

</style>
