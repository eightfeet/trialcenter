<template>
  <div class="modal-mask" v-show="show" transition="modal">
    <div class="modal-wrapper">
      <div class="modal-container pr">
        <div v-show="closeicon" class="icon-cancel gray fz-lm modal-close" v-touch:tap="show = false"></div>

        <div class="modal-header">
          <slot name="header">
            default header
          </slot>
        </div>

        <div class="modal-body">
          <slot name="body">
            default body
          </slot>
        </div>

        <div class="modal-footer">
          <slot name="footer">
            default footer
            <button class="modal-default-button"
              v-touch:tap="show = false">
              OK
            </button>
          </slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import coerceBoolean from '../utils/coerceBoolean.js'
export default {
  props: {
    show: {
      type: Boolean,
      required: true,
      twoWay: true
    },
    closeicon: {
      type: Boolean,
      coerce: coerceBoolean,
      default: true
    }
  }
}
</script>

<style lang="less">
.modal-mask {
position: fixed;
z-index: 9998;
top: 0;
left: 0;
width: 100%;
height: 100%;
background-color: rgba(0, 0, 0, .5);
display: table;
transition: opacity .3s ease;
}
.modal-close{
 font-size: 1.5rem;
 position: absolute;
 width: 2.5rem;
 height: 2.5rem;
 line-height: 2.5rem;
 text-align: center;
 right: 0;
}
.modal-close:before{
  vertical-align: middle;
  color:#ccc;
}
.modal-wrapper {
position: relative;
display: table-cell;
vertical-align: middle;
}

.modal-container {
width:90%;
margin: 0px auto;
background-color: #fff;
border-radius: .3rem;
box-shadow: 0 2px 8px rgba(0, 0, 0, .33);
transition: all .3s ease;
font-family: Helvetica, Arial, sans-serif;
}

.modal-body {
margin: .8rem auto;
width: 96%;
}

.modal-default-button {
float: right;
}

/*
* the following styles are auto-applied to elements with
* v-transition="modal" when their visiblity is toggled
* by Vue.js.
*
* You can easily play with the modal transition by editing
* these styles.
*/

.modal-enter, .modal-leave {
opacity: 0;
}

.modal-enter .modal-container,
.modal-leave .modal-container {
-webkit-transform: scale(1.1);
transform: scale(1.1);
}
</style>
