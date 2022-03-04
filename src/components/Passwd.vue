<template>
  <div class="cell">
    <div class="tip-text">剪贴板已加密</div>
    <div class="login-box">
      <div class="input-group">
        <span class="input-group-label">密码</span>
        <input type="password" placeholder="剪贴板查看密码" class="input-group-field">
        <div class="input-group-button">
          <input type="button" value="读取" class="button">
        </div>
      </div>
      <div class="text-center">
        <a href="/" class=" w-100">还没有剪贴板，去创建一个&gt;&gt;</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Passwd"
}
</script>

<style scoped>
.cell {
  flex: auto;
  font-size: 28px;
}

.login-box {
  display: inline-block;
  margin: 100px auto 180px auto;
  min-height: 200px;
  font-size: 16px;

}
.input-group {
  display:flex;
  min-height: 2rem;
  margin-bottom:1rem;
  -ms-flex-align:stretch;
  align-items:stretch
}

.input-group-button, .input-group-button a, .input-group-button button, .input-group-button input, .input-group-button label, .input-group-field, .input-group-label {
  margin:0;
  white-space:nowrap
}
.input-group-label {
  padding:0 1rem;
  border:1px solid #cacaca;
  background:#e6e6e6;
  color:#0a0a0a;
  text-align:center;
  white-space:nowrap;
  display:flex;
  -ms-flex:0 0 auto;
  flex:0 0 auto;
  align-items:center
}

.input-group-field {
  border-radius:0;
  -ms-flex:1 1 0px;
  flex:1 1 0px;
  height:auto;
  min-width:0
}
.input-group-button {
  padding-top:0;
  padding-bottom:0;
  text-align:center;
  display:-ms-flexbox;
  display:flex;
  flex:0 0 auto
}
.input-group-button a, .input-group-button button, .input-group-button input, .input-group-button label {
  height:auto;
  align-self:stretch;
  padding-top:0;
  padding-bottom:0;
  font-size:1rem
}
</style>