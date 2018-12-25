<template>
  <div>
    <div  :class="{ a: isA, b: isB,c: isC, d: isD ,e: isE, f: isF,g: isG, h: isH  }" class="div1" id="div1">
      <div id="1" class="div1_1">
        <!--<AppGood></AppGood>-->
        <app-good></app-good>
        <component :is="vcom1"></component>
      </div>
      <div id="2" class="div1_2">
        <component :is="vcom2"></component>
      </div>
      <div id="3" class="div1_3">
        <component :is="vcom3"></component>
      </div>
      <div id="4" class="div1_4">
        <component :is="vcom4"></component>
      </div>
    </div>
    <button style="margin-top: 600px" @click="next">下一张</button>
    <button style="margin-top: 600px" @click="last">上一张</button>
  </div>
</template>
<script>
  import V0 from './components/v0'
  import V1 from './components/v1'
  import V2 from './components/v2'
  import V3 from './components/v3'
  import V4 from './components/v4'
  import V5 from './components/v5'
  import V6 from './components/v6'
  import V7 from './components/v7'
  import AppGood from './components/AppGood'

  export default {
    data(){
      return{
        isA:false,
        isB:false,
        isC:false,
        isD:false,
        isE:false,
        isF:false,
        isG:false,
        isH:false,
        count:0,
        ccount:0,
        vcom1:'V1',
        vcom2:'',
        vcom3:'',
        vcom4:'',
        comCount:7//只需更改此处数据（组件的数量）即可
      }
    },
    components:{
      V0,
      V1,
      V2,
      V3,
      V4,
      V5,
      V6,
      V7,
      AppGood
    },
    name: 'App8',
    methods:{
      next(){
        var comcount=this.comCount
        this.count++
        var num=this.count
        if(num<=0){
          var rnum=-num
          var com
          if((rnum%comcount)==0){
            com=1
          }else{
            com=(comcount+1)-(rnum%comcount)//组件数
          }
          if(rnum%4==0){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=true
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
            if(num==0){
              this.vcom1="V"+1
            }
            this.vcom1="V"+com
          }else if(rnum%4==1){
            this.isA=false
            this.isB=false
            this.isC=true
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
            this.vcom4="V"+com
          }else if(rnum%4==2){
            this.isA=false
            this.isB=true
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
            this.vcom3="V"+com
          }else if(rnum%4==3){
            this.isA=true
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
            this.vcom2="V"+com
          }
        }else {
          this.ccount++
          var cnum=this.ccount
          if(this.ccount==comcount){
            this.ccount=0
            cnum=0
          }
          if(num%4==1){
            this.vcom2="V"+(cnum+1)
            this.isA=true
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
          }else if (num%4==2){
            this.vcom3="V"+(cnum+1)
            this.isA=false
            this.isB=true
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
          }else if (num%4==3){
            this.vcom4="V"+(cnum+1)
            this.isA=false
            this.isB=false
            this.isC=true
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
          }else if(num%4==0){
            this.vcom1="V"+(cnum+1)
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=true
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=false
          }
        }

      },
      last(){
        this.count--
        var num=this.count
        var comcount=this.comCount
        if(num>-1){
          this.ccount--
          var cnum=this.ccount
          if(this.ccount==-1){
            this.ccount=comcount-1
            cnum=comcount-1
          }
          if(num%4==0){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=true
            this.isF=false
            this.isG=false
            this.isH=false
            this.vcom1="V"+(cnum+1)
          }else if(num%4==1){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=true
            this.isG=false
            this.isH=false
            this.vcom2="V"+(cnum+1)
          }else if(num%4==2){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=true
            this.isH=false
            this.vcom3="V"+(cnum+1)
          }else if(num%4==3){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=true
            this.vcom4="V"+(cnum+1)
          }
        }
        else {
          var rnum=-num
          var com=comcount+1+(num%comcount)
          var ccom=com
          if(ccom==(comcount+1)){ccom=1}
          if(rnum%4==0){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=true
            this.isF=false
            this.isG=false
            this.isH=false
            this.vcom1="V"+ccom
          }else if(rnum%4==1){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=false
            this.isH=true
            this.vcom4="V"+ccom
          }else if(rnum%4==2){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=false
            this.isG=true
            this.isH=false
            this.vcom3="V"+ccom
          }else if(rnum%4==3){
            this.isA=false
            this.isB=false
            this.isC=false
            this.isD=false
            this.isE=false
            this.isF=true
            this.isG=false
            this.isH=false
            this.vcom2="V"+ccom
          }
        }
      }
    }
  }
</script>

<style scoped>
  div{
    width: 200px;
    height: 200px;
    margin: 0 auto;
    /*修改基本样式*/
  }
  .div1{
    margin-top: 100px;
    transform: perspective(400px) rotatex(0deg) rotatey(0deg);
    /*拥有近大远小透视效果*/
    transform-style: preserve-3d;
    /*设置为3d空间*/
    position: relative;
    /*border:1px solid #000000;*/
    /*animation: xuanzhuan 2s cubic-bezier(0.0,0.0,0.0,0.0)  forwards;*/
    /*旋转动画*/
  }
  @-webkit-keyframes xuanzhuan{
    from{
      transform:perspective(700px) rotatex(0deg);
    }
    to{
      transform:perspective(500px) rotatex(-90deg);
    }
  }
  @-webkit-keyframes xuanzhuan2{
    from{
      transform:perspective(700px) rotatex(-90deg);
    }
    to{
      transform:perspective(500px) rotatex(-180deg);
    }
  }
  @-webkit-keyframes xuanzhuan3{
    from{
      transform:perspective(700px) rotatex(-180deg);
    }
    to{
      transform:perspective(500px) rotatex(-270deg);
    }
  }
  @-webkit-keyframes xuanzhuan4{
    from{
      transform:perspective(700px) rotatex(-270deg);
    }
    to{
      transform:perspective(500px) rotatex(-360deg);
    }
  }
  @-webkit-keyframes rxuanzhuan{
    from{
      transform:perspective(700px) rotatex(-90deg);
    }
    to{
      transform:perspective(500px) rotatex(0deg);
    }
  }
  @-webkit-keyframes rxuanzhuan2{
    from{
      transform:perspective(700px) rotatex(-180deg);
    }
    to{
      transform:perspective(500px) rotatex(-90deg);
    }
  }
  @-webkit-keyframes rxuanzhuan3{
    from{
      transform:perspective(700px) rotatex(-270deg);
    }
    to{
      transform:perspective(500px) rotatex(-180deg);
    }
  }
  @-webkit-keyframes rxuanzhuan4{
    from{
      transform:perspective(700px) rotatex(-360deg);
    }
    to{
      transform:perspective(500px) rotatex(-270deg);
    }
  }

  .div1 div{
    position: absolute;
    font-size: 80px;
    /*line-height: 200px;*/
    /*text-align: center;*/
    top: 0;
    left: 0;
    /*内部样式*/
  }
  .div1_1{
    transform: translatez(100px);
    background-color: red;
    /*向前移动100像素，作为最前面的面*/
  }
  .div1_2{
    transform: rotatex(90deg) translatez(100px);
    background-color:green;
    /*绕x轴旋转90度，在z轴正方向移动100像素，作为上面的面*/
    /*注：旋转时坐标系会跟着一起旋转，z轴原来是垂直屏幕向外的，绕x轴旋转90度以后就是在屏幕上向上的方向*/
  }
  .div1_3{
    transform: rotatex(180deg) translatez(100px);
    background-color: blue;
    /*绕x轴旋转180度，这时z轴垂直屏幕向内，在z轴正方向移动100像素，作为后面的面*/
  }
  .div1_4{
    transform: rotatex(270deg) translatez(100px);
    background-color: purple;
    /*绕x轴旋转270度，这时z轴向下，在z轴正方向移动100像素，作为下面的面*/
  }
  .a{
    animation: xuanzhuan 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards  ;
  }
  .b{
    animation: xuanzhuan2 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards  ;
  }
  .c{
    animation: xuanzhuan3 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards  ;
  }
  .d{
    animation: xuanzhuan4 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards  ;
  }
  .e{
    animation: rxuanzhuan 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards;
  }
  .f{
    animation: rxuanzhuan2 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards;
  }
  .g{
    animation: rxuanzhuan3 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards;
  }
  .h{
    animation: rxuanzhuan4 1s cubic-bezier(0.0,0.0,0.0,0.0)  forwards;
  }
</style>
