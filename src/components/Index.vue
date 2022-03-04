<template>
  <div class="cell">
    <div class="login-box">
      <div class="input-group">
        <input type="text" placeholder="剪切板名称, 默认随机名称" class="input-group-field">
        <div class="input-group-button">
          <input type="button" value="进入" class="button">
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Index"
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
  /*border-radius:15px;*/
  border: #cacaca;
  display:flex;
  min-height: 3rem;
  width: 20rem;
  margin-bottom:1rem;
  font-size: 56px;
  align-items:stretch
}


.input-group-field {
  border-width: thin;
  border-radius: 15px 0 0 15px ;
  flex:1 1 0px;
  height:auto;
  min-width:0;
}
.input-group-button {
  border-width: thin;
  border-radius: 0 15px 15px 0 ;
  padding-top:0;
  padding-bottom:0;
  text-align:center;
  display:flex;
  flex:0 0 auto
}

.button{
  border-width: thin;
  border-radius: 0 15px 15px 0 ;
  background-color: darkturquoise;
}

</style>