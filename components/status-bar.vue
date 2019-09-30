<template>
	<view class="status-bar-style-default" :style="style">
		<view v-for="(item1, index1) in fontItems" class="status-bar-item-style-default status-bar-item-style" @click="statusEvent" :data-cur="item1.cur" :key="item1.cur">
			<text class="cuIcon-base status-bar-icon-style">{{ item1.icon }}</text>
		</view>
		<view v-if="hasContent" class="status-bar-item-search-style-default status-bar-item-content-style">
			<text class="cuIcon-base status-bar-icon-style status-bar-item-content-text-style">{{ titleText }}</text>
		</view>
		<view v-if="hasSearchButton" class="status-bar-item-search-style-default status-bar-item-style status-bar-item-search-style" @click="statusEvent" data-cur='search'>
			<text class="cuIcon-base status-bar-icon-style status-bar-item-search-text-style">&#xe65c;</text>
			<text class="cuIcon-base status-bar-icon-style status-bar-item-search-text-style">{{ titleText }}</text>
			<!-- <input v-if="hasSearchInput" class="status-search-input" type="text" name="" return-key-type="search" id="" value="" placeholder="搜索" /> -->
			<!-- <text class="cuIcon-base status-bar-text-style" @click="actionScan">&#xe689;</text> -->
		</view>
		<view v-for="(item2, index2) in backItems" class="status-bar-item-style-default status-bar-item-style" @click="statusEvent" :data-cur="item2.cur" :key="item2.cur">
			<text class="cuIcon-base status-bar-icon-style">{{ item2.icon }}</text>
		</view>
		<view v-if="hasPlaceholder" class="status-bar-item-style-default" :key="placeholder"></view>
	</view>
</template>

<script>
export default {
	data() {
		return {
			pageCur: 'basics'
		};
	},
	name: 'status-bar',
	props: {
		titleText: {
			type: [String],
			default: '搜索'
		},
		hasSearchButton: {
			type: [Boolean, String],
			default: false
		},
		hasContent: {
			type: [Boolean, String],
			default: false
		},
		hasPlaceholder: {
			type: [Boolean, String],
			default: false
		}, 
		fontItems: Array,
		backItems: Array
	},
	computed: {
		style() {
			var statusBar= this.StatusBar;
			var customBar= this.CustomBar;
			var bgImage = this.bgImage;
			var style = `height:${customBar}px;padding-top:${statusBar}px;`;
			if (this.bgImage) {
				style = `${style}background-image:url(${bgImage});`;
			}
			return style
		}
	},
	methods: {
		statusEvent(e) {
			// this.PageCur = e.currentTarget.dataset.cur;
			this.$emit('statusEvent', this.pageCur);
		}
	}
};
</script>

<style>
.status-bar-style-default {
	display: flex;
	/* #ifndef MP */
	width: 690rpx;
	/* #endif */
	/* #ifdef MP */
	width: 500rpx;
	/* #endif */
	align-items: center;
	position: fixed;
	left: 30rpx;
	height: 45px;
	z-index: 1024;
	justify-content: space-between;
	align-items: center;
	flex-direction: row;
}
.status-bar-item-style-default {
	display: flex;
	height: 45px;
	width: 45px;
	margin-left: 10px;
	border-radius: 50%;
	justify-content: center;
	align-items: center;
}
.status-bar-item-search-style-default {
	display: flex;
	flex: 1;
	height: 45px;
	margin-left: 10px;
	border-radius: 45px;
	justify-content: center;
	align-items: center;
	flex-direction: row;
}
</style>
