<template>
  <button
  v-bind:class="{
    mainbtn:true,
    iconfl:iconfixedleft,
    iconfr:iconfixedright,
    pr:true,
    style_a:stylea,
    style_b:styleb
  }"
  v-bind:style="{
    height:setheight+'rem'
    }"
  >
    <slot></solt>
  </button>
</template>

<script>
import coerceBoolean from '../utils/coerceBoolean.js'
export default {
  props: {
    iconfixedleft: {
      type: Boolean,
      coerce: coerceBoolean,
      default: false
    },
    iconfixedright: {
      type: Boolean,
      coerce: coerceBoolean,
      default: false
    },
    setstyle: {
      type: String,
      default: 'a'
    },
    setheight: {
      type: String,
      default: '2.5'
    },
    stylea: {
      type: Boolean,
      default: true
    },
    styleb: {
      type: Boolean,
      default: false
    }
  },
  ready () {
    const small = this.small
    if (small) {
      this.big = false
    }
    if (this.setstyle === 'a') {
      this.stylea = true
      this.styleb = false
    }
    if (this.setstyle === 'b') {
      this.styleb = true
      this.stylea = false
    }
  }
}
</script>

<style lang="less">
//## Gray and brand colors for use across Bootstrap.

//## Gray and brand colors for use across Bootstrap.

@gray-base:              #000;
@gray-darker:            lighten(@gray-base, 13.5%); // #222
@gray-dark:              lighten(@gray-base, 20%);   // #333
@gray:                   lighten(@gray-base, 33.5%); // #555
@gray-light:             lighten(@gray-base, 46.7%); // #777
@gray-lighter:           lighten(@gray-base, 93.5%); // #eee


//==Coloured
//
@cyan:                      #48c5c7;
@red:                      #e10000;
@orange:                   #ffaf00;
@white:                  #fff;
@blue:                    #007bed;



.cyan{color:                    @cyan; }
.red{ color:                      #e10000;}
.orange{ color:                   #feb028;}
.white{ color:                  #fff;}
.gray{color:#a7a7a7}
.blue{color: @blue;}

a.cyan:hover,a.cyan:visited,a.cyan:link{color: @cyan;}




//==Fontsize
//
@fz-s:              .833rem;  // 20 px
@fz:                 1rem; // 24 px
@fz-m:            1.16rem; // 28 px
@fz-ml:           1.25rem; // 30 px
@fz-l:              1.333rem; //  32 px
@fz-ll:             1.5rem; //  36px


  //==btn
  .style_a{
    background-color:@cyan;
    color:@white;
    border: 1px solid @cyan !important;
    &:active{
         background:@blue;
         border: 1px solid @blue;
    }&:focus{border: 1px solid @cyan;outline:none;}
  }
  .style_b{
    background-color:@white;
    color:@cyan;
    border: 1px solid @cyan;
    &:active{
         background:@cyan;
         border: 1px solid @cyan;
         color:@white;
    }&:focus{border: 1px solid @cyan;outline:none;}
  }
  
  .mainbtn{
      -webkit-border-radius: 0.3rem;
      -moz-border-radius: 0.3rem;
      border-radius: 0.3rem;
      text-align: center;
      width: 100%;
      font-weight: bold;
      font-size: @fz;
      display: block;
  }
  .mainbtn:before{
    vertical-align: middle;
    text-align: center;
  }
  a.mainbtn,a.mainbtn_disable,a.mainbtn_b{  }

  .iconfl:before{
    position: absolute;
    vertical-align: middle;
    text-align: center;
    left: 1rem;
    height:1rem;
    line-height: 1rem;
    top: 50%;
    margin-top:-0.5rem;
  }
  .al-l{
    padding-left:1rem;
    text-align: left;
  }
  .al-r{
    padding-right:1rem;
    text-align: right;
  }
  .iconfr:before{
    position: absolute;
    vertical-align: middle;
    text-align: center;
    right: 1rem;
    height:1rem;
    line-height: 1rem;
    top: 50%;
    margin-top:-0.5rem;
  }


</style>
