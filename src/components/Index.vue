<template>
  <div class="container">
    <div class="login-box center">
            <div class="input-group">
              <input type="text"  placeholder="剪切板名称, 默认随机名称" class="input-group-field" v-model:value="boardName"/>
              <button class="input-group-button" @click="enterBoard()" type="button">
                <span>进入</span>
              </button>
            </div>
    </div>
    <div class="intro-box">
      <p>File Helper 懂的都懂！</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "Index",
  data(){
    return{
      bardName:''
    }
  },
  methods:{
    enterBoard(){
        let url = '/' + this.boardName;
        console.log(url);
        window.location.href = url;
    }
  }
}
</script>

<style scoped>
.center {
  display: flex;
  align-content: center;
  align-items: center;
  /*margin: auto;*/
}

.container {
  font-size: 28px;
  height: 70vh;
  width: 90%;
  min-height: 70vh;
  margin-top: 5rem;
  display: flex;
  flex-direction: column;
}

.intro-box {
  width: 100vw;
  height: 50%;
  text-align:center;
    /*margin: auto;*/
}

.login-box {
  width: 100vw;
  height: 50%;
  font-size: 16px;
}

.input-group {
  display: flex;
  min-height: 3rem;
  width: 20rem;
  margin: auto;
  font-size: 56px;
  align-items: stretch
}


.input-group-field {
  border-width: thin;
  border-radius: 15px 0 0 15px;
  flex: 1 1 0px;
  /*height: auto;*/
}

input:focus {
  outline:none;
  box-shadow: 5px 2px 5px grey;
}


/***************************************/


.input-group-button {
  line-height: 1;
  min-height: 40px;
  background: #fff;
  color: #606266;
  text-align: center;
  outline: 0;
  margin: 0;
  padding: 12px 20px;
  font-size: 14px;
  color: white;
  background-color: #00a2ca;
  border: #00a2ca;
  border-radius: 0 15px 15px 0;
}
button:active{
  position: relative;
  top: 1px;
  left: 1px;
}
button:hover {
  background-color: #009a9a;
}
a:hover {
  color: hotpink;
}

</style>