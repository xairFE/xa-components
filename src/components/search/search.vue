<template>
  <div class="weui-search-bar" :class="{'weui-search-bar_focusing': isFocusing}">
    <form @click="searchClick" @submit.prevent="onSearch" class="weui-search-bar__form">
      <div class="weui-search-bar__box">
        <i class="iconfont icon-search"></i>
        <input ref="search" type="search" :value="value" @input="onInput" @blur="onBlur" class="weui-search-bar__input" placeholder="搜索" required="">
        <a @click="searchClear" href="javascript:" class="weui-icon-clear">×</a>
      </div>
      <label class="weui-search-bar__label" style="transform-origin: 0px 0px 0px; opacity: 1; transform: scale(1, 1);">
        <i class="iconfont icon-search"></i>
        <span>搜索</span>
      </label>
    </form>
    <a href="javascript:" @click="searchCancel" class="weui-search-bar__cancel-btn">取消</a>
  </div>
</template>

<script>
export default {
  data () {
    return {
      isFocusing: !!this.value
    }
  },
  props: {
    value: {
      type: String
    }
  },
  methods: {
    searchClick () {
      this.isFocusing = true
      this.$refs.search.focus()
    },
    searchClear () {
      this.$emit('input', '')
    },
    onInput (e) {
      this.$emit('input', e.target.value)
    },
    searchCancel () {
      this.$emit('input', '')
      this.isFocusing = false
      this.$emit('search')
    },
    onSearch () {
      this.$emit('search')
      this.$refs.search.blur()
    },
    onBlur () {
      if (!this.value) {
        this.isFocusing = false
      }
    }
  }
}
</script>

<style scoped>
  .weui-search-bar {
  position: relative;
  padding: 8px 10px;
  display: -webkit-box;
  display: -webkit-flex;
  display: flex;
  box-sizing: border-box;
  background-color: #EFEFF4;
}
.weui-search-bar:before {
  content: " ";
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  height: 1px;
  border-top: 1px solid #D7D6DC;
  color: #D7D6DC;
  -webkit-transform-origin: 0 0;
          transform-origin: 0 0;
  -webkit-transform: scaleY(0.5);
          transform: scaleY(0.5);
}
.weui-search-bar:after {
  content: " ";
  position: absolute;
  left: 0;
  bottom: 0;
  right: 0;
  height: 1px;
  border-bottom: 1px solid #D7D6DC;
  color: #D7D6DC;
  -webkit-transform-origin: 0 100%;
          transform-origin: 0 100%;
  -webkit-transform: scaleY(0.5);
          transform: scaleY(0.5);
}
.weui-search-bar.weui-search-bar_focusing .weui-search-bar__cancel-btn {
  display: block;
}
.weui-search-bar.weui-search-bar_focusing .weui-search-bar__label {
  display: none;
}
.weui-search-bar__form {
  position: relative;
  -webkit-box-flex: 1;
  -webkit-flex: auto;
          flex: auto;
  background-color: #EFEFF4;
}
.weui-search-bar__form:after {
  content: '';
  position: absolute;
  left: 0;
  top: 0;
  width: 200%;
  height: 200%;
  -webkit-transform: scale(0.5);
          transform: scale(0.5);
  -webkit-transform-origin: 0 0;
          transform-origin: 0 0;
  border-radius: 10px;
  border: 1px solid #E6E6EA;
  box-sizing: border-box;
  background: #FFFFFF;
}
.weui-search-bar__box {
  position: relative;
  padding-left: 30px;
  padding-right: 30px;
  height: 100%;
  width: 100%;
  box-sizing: border-box;
  z-index: 1;
}
.weui-search-bar__box .weui-search-bar__input {
  padding: 4px 0;
  width: 100%;
  height: 1.42857143em;
  border: 0;
  font-size: 14px;
  line-height: 1.42857143em;
  box-sizing: content-box;
  background: transparent;
}
.weui-search-bar__box .weui-search-bar__input:focus {
  outline: none;
}
.weui-search-bar__box .iconfont {
  position: absolute;
  left: 10px;
  top: 0;
  line-height: 28px;
  color:#aaa;
  font-size: 18px;
}
.weui-search-bar__box .weui-icon-clear {
  position: absolute;
  height:20px;
  width:20px;
  top: 4px;
  right: 4px;
  text-align: center;
  line-height: 21px;
  border-radius: 50%;
  font-size:18px;
  background-color: #ccc;
  color: #999;
}
.weui-search-bar__label {
  position: absolute;
  top: 1px;
  right: 1px;
  bottom: 1px;
  left: 1px;
  z-index: 2;
  border-radius: 3px;
  text-align: center;
  color: #9B9B9B;
  background: #FFFFFF;
}
.weui-search-bar__label span {
  display: inline-block;
  font-size: 14px;
  vertical-align: middle;
}
.weui-search-bar__label .iconfont {
  vertical-align: -2px;
  font-size: 18px;
}
.weui-search-bar__cancel-btn {
  display: none;
  margin-left: 10px;
  line-height: 28px;
  color: #09BB07;
  white-space: nowrap;
}
.weui-search-bar__input:not(:valid) ~ .weui-icon-clear {
  display: none;
}
input[type="search"]::-webkit-search-decoration,
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-results-button,
input[type="search"]::-webkit-search-results-decoration {
  display: none;
}
</style>

