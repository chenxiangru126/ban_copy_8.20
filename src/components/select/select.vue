<template>
 <div class="reg_wrap">
 <!-- 主体部分 -->
 <div class="reg_content">
    <div class="content_con">
        <div class="geren " @click="person_ban">
          <span>
              <img src="../../static/images/gerenw.png" alt="">
              <p class="geren_word">个人</p>
          </span>
        </div>
        <div class=" qiye" @click="com_ban">
          <span>
              <img src="../../static/images/qiyew.png" alt="">
              <p class="qiye_word">企业</p>
          </span>
        </div>
    </div>

 </div>

</div>    
</template>
<script>
export default {




  methods:{
    person_ban(){
//       this.$router.push('/real')

        this.util.ajax.post('/admin/sysUserReal/getId.do').then(e => {
//            debugger;
            if( e.code == 500){
//                   未实名
                this.$router.push('/real')
            }else if( e.code == 200){
//                this.$router.push('/order_create?id='+id+'&type=1&count=1')
                this.$router.push('/ban_copy')

            }
        })
// .catch()
    },
    com_ban(){ //判断企业是否实名
         this.util.ajax.post('/admin/sysUserReal/getId.do').then(e => {
            if( e.code == 500){
                //未实名
                this.$router.push('/qiye')
            }else if( e.code == 200){
                // 已实名
                this.$router.push('/ban_copy')

            }
        })
    }
  }
    
}
</script>
<style lang="less">
@import 'select.less';
</style>


