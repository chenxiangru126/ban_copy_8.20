<template>
<div class="switch">


</div>
    
</template>

<script>
import util from '../../libs/util'
/* 
1.判断是否是第一次，浏览版权说明页面，如果不是，页面不显示，得到状态值，这个是前提
2.判断是否实名认证，如果实名认证的话，得到状态值，
   跳转到上传页面，没有实名认证的话跳转到选择类型页面，得到状态值
*/
export default {
//  data(){
////    return{
////      isIos: isAndroidOrIos() == 1 ? true : false,
////    }
//  },
//  computed: mapState(
//    ['title_name','route_name']
//  ),
    created(){
     var that = this

    },
    mounted(){
    // 1.第一种判断是否注册app
    //判断是否有token

         this.util.ajax.post('/admin/users/bqCount.do').then(e=>{
            
         if(e.code == 200){
           let state = e.data.status

           if(state == 0){

             this.Toast('请登录')
             iosObject.goLogin();
//                 alert('请登录。。。')
//               alert('0')
           }else{
              if(state ==2){
//                  alert('2')
               this.$router.push('/explain')
              }else{
                if(state == 4){
//                    alert('4')
                   this.$router.push('/ban_copy')
                }else{
                    this.$router.push('/select')
                }

              } 


              

           }


               
           }

        

         })
     
    // 2.第二种情况是判断有注册没有点击我知道页面
    // 3.没有实名认证页面
    // 4.已实名认证页面
    },
    data(){
      return{

          token:null,
      }
    },
    methods:{
            

    }
    
}
</script>

 
 <style scoped>
  @import 'switch.less';
 </style>
 
 