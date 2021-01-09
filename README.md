# categories
uni-app仿美团分类组件，可用于商品分类等。



## 组件使用方式

将 **long-categories** 复制到 uni-app项目中的 **components**目录即可

```vue
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
```

## list数据结构

| 名称        | 类型   | 说明                                          |
| ----------- | ------ | --------------------------------------------- |
| id          | String | 数据唯一标志，可根据需要更改                  |
| name        | String | 左侧分类显示名称，可根据需要修改              |
| selectedIds | Object | 存放右侧选择的元素id                          |
| children    | Array  | 右侧分类列表，详细数据结构见 children结构描述 |

### children数据结构

| 名称     | 类型    | 说明                         |
| -------- | ------- | ---------------------------- |
| id       | String  | 元素唯一标志                 |
| name     | String  | 元素显示名称，可根据需要修改 |
| disabled | Boolean | 元素是否可选中               |
| checked  | Boolean | 元素是否被选中               |



## 属性

| 名称        | 类型             | 默认值 | 说明                        |
| ----------- | ---------------- | ------ | --------------------------- |
| list        | Array            | []     | 列表数据                    |
| maxSelected | [String, Number] | -1     | 最大选择数，默认为 -1不限制 |

## 事件

| 名称   | 返回值 | 说明               |
| ------ | ------ | ------------------ |
| change | Array  | 返回选中的数据数组 |

## 方法

| 名称        | 说明                                         |
| ----------- | -------------------------------------------- |
| getValues() | 获取选中的数据数组，和change事件中的数据一致 |

## 使用示例

详细代码 [Demo](https://github.com/songhailong8174/categories)

## 插件截图

![img](https://cdn.jsdelivr.net/gh/songhailong8174/images/img/1.png)

![img](https://cdn.jsdelivr.net/gh/songhailong8174/images/img/2.png)

![img](https://cdn.jsdelivr.net/gh/songhailong8174/images/img/3.png)

PS：如有问题可联系QQ（1365763165）或者提issure，如果帮到你了还请不要吝啬给个 [Star](https://github.com/songhailong8174/categories)哈

