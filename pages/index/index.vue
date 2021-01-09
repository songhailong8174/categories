<template>
	<view class="content">
		<view>
			<view class="">
				<view>最多选 {{ max }} 个</view>
				<view>已选 {{ count }} 个</view>
			</view>
			<long-categories
				:list="list"
				:maxSelected="max"
				@change="change"
			>
			</long-categories>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [],
				count: 0,
				max: 10
			}
		},
		onLoad() {
			this.init()
		},
		methods: {
			init () {
				for (let i = 0; i < 10; i++) {
					let item = {
						id: `c-${ i }`,
						name: `分类-${ i }`,
						children: [],
						selectedIds: {}
					}
					for (let j = 0; j < 10; j++) {
						item.children.push({
							id: `item-${ i }-${ j }`,
							name: `元素${ j }`,
							disabled: ( j > 2 && j < 5),
							checked: false
						})
					}
					this.list.push(item)
				}
			},
			change (data) {
				this.count = data.length
				console.log(data)
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
