<template>
  <header>
    <div class="container center">
      <div v-if="showLogo" class="cell center logo">
        <div>
          <div class="slogan"><a href="/"><i class="iconfont icon-clipboard"></i>网络剪贴板</a></div>
        </div>
      </div>

      <div v-if="isBoard" class="board-opt center">
        <div class="">
          <label class="expire-time op-item">
            有效期：
            <select @change="selectExpiredTime($event)">
              <option v-for="itm in selectItm" :value="itm.value" :key="itm.value">{{ itm.title }}</option>

            </select>
          </label>
          <label>
            密码：
            <a href="javaScript::" v-on:click="setPasswd" title="点击更换密码">
              {{ passwd ? "已设置" : "未设置" }}
            </a>
          </label>
        </div>
      </div>

      <div v-if="isBoard" class="center right-box">
        <div class="opt-box">
          <button class="delete" v-on:click="deleteBoard()">删除</button>
          <button class="save" v-on:click="saveBoard()">保存</button>
        </div>
      </div>

    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      showLogo: true,
      isBoard: true,
      passwd: false,
      expiredTime: 259200,
      selected: 259200,
      selectItm: [
        {
          title: "1小时",
          value: 3600,
        },
        {
          title: "6小时",
          value: 21600,
        },
        {
          title: "1天",
          value: 86400,
        },
        {
          title: "3天",
          value: 259200,
        },
        {
          title: "一周",
          value: 604800,
        },
        {
          title: "一个月",
          value: 2592000,
        },
        {
          title: "三个月",
          value: 7776000,
        },
        {
          title: "六个月",
          value: 15552000,
        },
        {
          title: "一年",
          value: 31536000,
        },
      ]
    }
  },
  mounted() {

    window.onresize = () => {
      this.handleResize()
    }
    this.handleResize()
  },
  methods: {
    handleResize() {
      console.log('width:', document.body.clientWidth);
      this.fullWidth = document.documentElement.clientWidth;
      if (this.fullWidth < 450) {
        this.showLogo = false;
      } else {
        this.showLogo = true;
      }
    },
    setPasswd() {
      this.passwd = !this.passwd
    },
    selectExpiredTime(event) {
      console.log('select event:', event.target.value);
      this.selected = event.target.value
    },
    saveBoard() {
      console.log("click save!")
    },
    deleteBoard() {
      console.log('click delete！')
    }
  }

}
</script>

<style scoped>
.container {
  width: 100%;
  /*position: absolute;*/
  position: fixed;
  background-color: white;
  z-index: 999;
  display: flex;
  flex-direction: row;
  height: 4rem;
  top: 0px;
  left: 0px;
  box-shadow: 5px 2px 5px grey;
}

/*.logo{*/
/*  */
/*}*/

.center {
  display: flex;
  align-content: center;
  align-items: center;
}

.cell {
  margin: 3%;
  float: left;
  height: 80%;
  width: auto;
}

.right-box {
  position: absolute;
  right: 0;
  float: right;
  margin-right: 3%;
  display: flex;
  flex-direction: row-reverse;
  align: right
}

.board-opt {
  width: 60%;
}


.expire-time {

}

.expire-time select {
  width: auto;
  height: 2rem;
}

.delete {
  color: red;
}

.right-box {

}

right-box {

}

button {
  width: 4rem;
  height: 2rem;
  border: none;
  font-size: large;
}

.save {
  background-color: #eaeaea;
  margin-left: 0.8rem;
}
</style>