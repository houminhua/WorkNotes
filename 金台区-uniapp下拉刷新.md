1.page.json 中开启

```json
	 {
      "path": "pages/audit/auditList",
      "style": {
        "navigationBarTitleText": "待审核",
        "enablePullDownRefresh": true,   // 开启下拉刷新
        "app-plus": {
          // "titleNView": false
        }
      }
    },


    return{
    	status: 0,    
    }

	<uni-loading v-if="!contentBoole" :status="status"  color="#888"  />



	import uniLoading from '@/components/mix-load-more/mix-load-more';
```

2.下拉/上拉

```json
  下拉  onPullDownRefresh() {
        let _self =this
        _self.pageno=1   //页数 
        setTimeout(function() {
            uni.stopPullDownRefresh();
    	_self.getlist(0)
    }, 1000);
    },

  上拉  onReachBottom() {
        let _self = this
        _self.status = 1
        _self.pageno++
        uni.showNavigationBarLoading()   //show  显示导航条加载动画
    setTimeout(function() {
        _self.getlist(1)
        _self.status = 0
        uni.hideNavigationBarLoading()  //
    }, 1000);
    },
				
		//	向请求数据函数中传入0/1区分上拉/下拉		
			
    if(num==0){
        this.listhome =arrbar
        if(arrbar.length==0){
            this.contentBoole=true  // 显示暂无数据
        }else if(arrbar.length<8){
            this.status=2  //2 无数据   *第一次数据加载完成*
        }
    }else{
        if(arrbar.length==0){
            this.status=2    
        }
        this.listhome =   this.listhome.concat(arrbar) 
    //数组相加
    }
```

3.刷新组件

```html
<template>
	<view class="mix-load-more">
		<image 
			class="mix-load-icon"
			src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAB4AAAAeCAYAAAA7MK6iAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyhpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTMyIDc5LjE1OTI4NCwgMjAxNi8wNC8xOS0xMzoxMzo0MCAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTUuNSAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6OUJCRjNGOEQ1RDNBMTFFOUFERjY5MEU0MTg5MjY0NDgiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6OUJCRjNGOEU1RDNBMTFFOUFERjY5MEU0MTg5MjY0NDgiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDo5QkJGM0Y4QjVEM0ExMUU5QURGNjkwRTQxODkyNjQ0OCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDo5QkJGM0Y4QzVEM0ExMUU5QURGNjkwRTQxODkyNjQ0OCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/Pkf/QQsAAAHYSURBVHjavFfRcYJAEOVu8h87SFJBSAUJNGCsIKQCsQK1AkkHpAKwAaUE7YB0kFRg3prFcWAPTziyM+uJHPvuvV32TuVZ2na79TG8wWkc8Ui2g3/z+BkEwc4mnrIAXGCYMpiN0SISLGDZCRiArxhW8Huvm5XwGRaQSzd1C8usB6jHz2aINbdijIkp59KlpWD+bmTMTNtA13AK8IRAipy+82/rlucijt1kzDnNWgBjAJUXCpHkTeBjw5RJlfMT8GazKZVSd8JkKpDkGl2xgJgLs1FwiPVwkppkcAVKxs/MpIKrJD8CHw6HWJK3C2gNXMr79AhMHQlsb4UJsYNqlmKMCJMYRwa2ZV9UjiGxjjRk9oUbucN3uBGLMLWhB+8cAjdiUWo1Ph4FiZwBG2L52vsHg7Q/9WvK8d6w9zozqJrUrzXvnw0pXAJDbmoaAXz5dxksboBOOXiuzaW+nToGLzAU57uTBDDmhj+Yaaq6evLZVoMCS8mv5OZdZhCz2RZpH/4YhDGzNrFLwDxznXMlHH3mF/ou+b5vd+t72LM6Q1ufqy2YC69pUHTKsdBpJnjNvizjvHQuLgE8D8OQCmppeM/PrXAidcuftogPDiPaTmlB1ANYoavsV4ABAGz+xJ8bzHJJAAAAAElFTkSuQmCC"
			v-show="status === 1"
		>
		</image>
		<text class="mix-load-text">{{text[status]}}</text>
	</view>
</template>

<script>
	export default {
		name: "mix-load-more",
		props: {
			status: {
				//0加载前，1加载中，2没有更多了
				type: Number,
				default: 0
			},
			text: {
				type: Array,
				default () {
					return [
						'上拉显示更多',
						'正在加载...',
						'没有更多数据了'
					];
				}
			}
		}
	}
</script>

<style>
	.mix-load-more{
		display: flex;
		flex-direction: row;
		justify-content: center;
		align-items: center;
		height: 90upx;
		padding-top: 10upx;
	}
	.mix-load-icon{
		display: block;
		width: 36upx;
		height: 36upx;
		margin-right: 12upx;
		animation: load 1.2s cubic-bezier(.37,1.08,.7,.74) infinite;
	}
	.mix-load-text{
		font-size: 28upx;
		color: #888;
	}

	@-webkit-keyframes load {
		0% {
			transform: rotate(0deg);
		}

		100% {
			transform: rotate(360deg);
		}
	}
</style>
```

