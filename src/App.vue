<template>

    <div id="app"  v-bind:class="{ context:showHead,context2:!showHead }">
      <transition name="slide-fade">
        <div class="head" v-show="showHead">
        头部菜单---展开
        </div>
      </transition>
      <transition name="slide-fade">
        <div class="head2" v-show="!showHead">
        头部菜单--收缩
        </div>
      </transition>


        <div>
                <div>内容1111111</div>
                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容1111111</div>
                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容1111111</div>
                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容1111111</div>
                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容1111111</div>
                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
                                <div>内容内容</div>
                <div>内容内容</div>
        </div>

    <transition name="slide-fade">
      <div class="foot" v-show="showHead">
        <van-row   gutter="20">
           scrollHeight:{{scrollHeight}} --scrollTop:{{scrollTop}}--clientHeight:{{clientHeight}}--lastScrollTop:{{lastScrollTop}} 
          <van-col  span="8"><van-button class="bt-class" round  icon="star-o" type="default" /></van-col>
          <van-col  span="8"> <van-button class="bt-class" round  icon="wap-home-o" type="default" /></van-col>
          <van-col  span="8"><van-button class="bt-class" round  icon="manager-o" type="default" /></van-col>
        </van-row>
        
      </div>
    </transition>
    </div>

</template>

<script>
import Vue from 'vue';
import { Button } from 'vant';
import { Icon } from 'vant';
import { Col, Row } from 'vant';
import { Popup } from 'vant';

Vue.use(Popup);

Vue.use(Col);
Vue.use(Row);
Vue.use(Icon);
Vue.use(Button);
export default {
  name: 'app',
 data() {
    return {
      showHead:true,
      scrollHeight:0,
      scrollTop:0,
      clientHeight:0,
      lastScrollTop:0
    };
  },
  methods: {
			scrollHandle () {
        alert("ssss")
				// 获取页面页面的滚动高度
				let scrollHeight = document.documentElement.scrollHeight || document.body.scrollHeight  
				// 获取页面滚动距离顶部的高度,  window.pageYOffse 兼容苹果
		   	let scrollTop = document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop  
		    	// 获取页面的可视高度
	    	let clientHeight = document.documentElement.clientHeight || document.body.clientHeight
         this.scrollHeight=scrollHeight;
         this.scrollTop=scrollTop;
         this.clientHeight=clientHeight;
         //内容向上走 scrollTop 变大  每变大200,将顶部收缩
         if(scrollTop - this.lastScrollTop > 20){
           this.lastScrollTop = scrollTop;
           this.showHead = false;
         }

         //内容向下走 scrollTop 变小  每变小200,将顶部展开
         if(this.lastScrollTop - scrollTop   > 20){
           this.lastScrollTop = scrollTop;
           this.showHead = true;
         }

				// 我们可以在这里判断页面的滚动是否到了底部
				// if (scrollTop + clientHeight === scrollHeight) {		 		
        //  }
        
				 // 当然我们也可以滚动距离底部还有一定距离的时候执行加载
				//  if (scrollTop + clientHeight >= scrollHeight - 20) {
        //   }
          
			}
  },
  destroyed () {
	 		// 页面卸载时移除监听事件
	 		window.removeEventListener('scroll', this.scrollhandle, true)
     },
  created () {
		window.addEventListener('scroll', this.scrollHandle, true)
	}

}
</script>

<style scoped>
.head {
/*头部浮动在最上方，且在最外层，这个是收缩之前的头部*/
  opacity: 1;
  position: fixed;
  height: 50px;
  left: 0px;
  right: 0px;
  top: 0px;
  background-color: rgb(181, 181, 233);
  z-index: 999;
}
.head2 {
/*头部浮动在最上方，且在最外层，这是收缩之后的头部*/
  opacity: 1;
  position: fixed;
  height: 25px;
  left: 0px;
  right: 0px;
  top: 0px;
  background-color: rgb(181, 181, 233);
  z-index: 999;
}
.context {
/*主div下方空出50px,防止被头部遮挡 */
  right: 5px;
   margin-top: 50px;
}
.context2 {
/*主div下方空出50px,防止被头部遮挡  与.head配套使用 */
  right: 5px;
   margin-top: 25px;
}
.bt-class{
        border:0px;
        background-color: rgb(208, 208, 219);
}
.foot {
 /*底部浮动在最下方，且在最外层*/
  text-align:center;
  opacity: 1;
  position: fixed;
  
  left: 0px;
  right: 0px;
  bottom: 0px;
  background-color: rgb(218, 218, 231);
  z-index: 999;
}
.slide-fade-enter-active {transition: all .3s ease;}
.slide-fade-leave-active {transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);}
.slide-fade-enter, .slide-fade-leave-to{transform: translateX(5px);opacity: 0;}

    

</style>
