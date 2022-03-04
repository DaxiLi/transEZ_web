<template>
  <div id="app">
    <div class="container center">

      <!--      <div class="grid-container">-->
      <!--        <div class="grid-x grid-margin-x">-->
      <!--          <div class="cell large-12">-->
      <!--            <div class="float-left note-tab" style="display: block;">-->
      <!--              <span title="切换到文本" class="active">剪贴板文本</span>-->
      <!--              <span title="切换到文件" class="">-->
      <!--                文件<small>（ 0 个 ）</small>-->
      <!--              </span>-->
      <!--            </div>-->
      <!--            <a href="javascript:;" title="展开/缩起剪贴板区域" class="float-right note-extend-btn">-->
      <!--              <i class="iconfont icon-angle-double-right"></i>-->
      <!--            </a>-->
      <!--          </div>-->
      <!--          <div class="cell large-10 note-box large-10">-->
      <!--            <div class="note-wrapper">-->
      <!--              <pre class="pre-box"></pre>-->
      <!--              <textarea id="noteContent" placeholder="使用后请主动删除剪贴板"></textarea></div>-->
      <!--            <div class="note-wrapper file-box" style="display: none;"><p class="limit-tip">-->
      <!--              最多上传10个文件，单文件50MB内，总大小500MB内，<br>-->
      <!--              <span style="color: red;">为提高剪贴板资源利用率，所上传文件有效期为7天，到期将自动删除。</span>-->
      <!--            </p>-->
      <!--              <div id="dragBox" class="drag-box"><input type="file" id="filePicker" class="file-picker">-->
      <!--                <div class="tip-word">-->
      <!--                  <i class="iconfont icon-plus"></i>-->
      <!--                  请将文件至此或点击上传（全格式）-->
      <!--                </div>-->
      <!--              </div>-->
      <!--              <div>-->
      <!--                <ul class="ul-file" style="display: none;"></ul>-->
      <!--              </div>-->
      <!--            </div>-->
      <!--          </div>-->
      <!--          <aside class="cell large-2 small-12 aside">-->
      <!--            <button data-clipboard-target="#noteContent" class="button success js-copy expanded show-for-large"-->
      <!--                    style="color: rgb(255, 255, 255);">复制剪贴板文本-->
      <!--            </button>-->
      <!--            <div class="note-info">-->
      <!--              <ul class="no-bullet">-->
      <!--                <li title="2022-03-03 19:42:12"><b>创建时间：</b> <span>2022-03-03 19:42:12</span></li>-->
      <!--                <li title="2022-03-03 20:28:04"><b>更新时间：</b> <span>2022-03-03 20:28:04</span></li>-->
      <!--                <li title="2022-03-03 20:28:04"><b>上次查看：</b> <span>2022-03-03 20:23:29</span></li>-->
      <!--                <li title="有效期内都有效"><b>有效期：</b> <span style="color: red;">3天内</span></li>-->
      <!--                <li title="点击查看访问详情"><b>查看次数：</b> <a href="javascript:;">2次</a></li>-->
      <!--              </ul>-->
      <!--            </div>-->
      <!--            <div class="link-box">-->
      <!--              <div class="link-tab clearfix"><span class="">只读链接</span> <span class="active">剪贴板链接</span></div>-->
      <!--              <div class="qrcode-box">-->
      <!--                <div id="qrcodeBox" title="手机扫码打开">-->
      <!--                  <div style="display: none;">-->
      <!--                    <div><img src="" alt="只读二维码" data-clipboard-text="" data-clipboard-tip="已复制只读链接" title="点击复制只读链接"-->
      <!--                              class="js-copy">-->
      <!--                      <span>点击复制只读链接</span>-->
      <!--                    </div>-->
      <!--                  </div>-->
      <!--                  <div><img src="" alt="二维码" data-clipboard-text="" data-clipboard-tip="已复制剪贴板链接" title="点击复制剪贴板链接"-->
      <!--                            class="js-copy">-->
      <!--                    <span>点击复制剪贴板链接</span>-->
      <!--                  </div>-->
      <!--                </div>-->
      <!--              </div>-->
      <!--            </div>-->
      <!--            <div title="如内容非法请举报，举报后将立即无法查看剪贴板" class="report-box">-->
      <!--              <a href="javascript:;">-->
      <!--                <i class="iconfont icon-shuangse-weifajubao"></i>-->
      <!--                非法内容举报-->
      <!--              </a>-->
      <!--            </div>-->
      <!--          </aside>-->
      <!--        </div>-->
      <!--      </div>-->
      <!--      -->


      <div class="show-box">

        <!--        <div class="top-box">-->
        <!--          <div class="button center">-->
        <!--            文本-->
        <!--          </div>-->
        <!--          <div class="button file-box center">-->
        <!--            文件({{ fileNum }})-->
        <!--          </div>-->
        <!--        </div>-->


        <div class="float-left note-tab">
          <span v-on:click="changeTextFile(true)" title="切换到文本" v-bind:class="{active: showText}">剪贴板文本</span>
          <span v-on:click="changeTextFile(false)" title="切换到文件"
                v-bind:class="{active: !showText}">文件<small>（ 0 个 ）</small></span>
        </div>


        <div class="detail-box">
          <div v-if="showTxt" class="detail-txt">
            <div>


              <div v-show="showText" class="expandingArea " id="textarea">
                <pre><span></span><br></pre>
                <textarea></textarea>
              </div>


              <div v-show="!showText" class="note-wrapper file-box"><p class="limit-tip">
                最多上传10个文件，单文件50MB内，总大小500MB内，
                当前已传 <b>0</b> 个文件，共计 <b>0.0KB</b>， 还能上传 <b>10</b>
                个文件。<br>
                为保障数据安全，建议添加密码压缩文件后上传，小文件打包上传，数据请自行多重备份。<br> <span
                  style="color: red;">上传文件有效期为7天，到期将自动删除。</span></p>
                <div id="dragBox" v-bind:class="{'drag-box': true , 'drag-active':dragActive}">
                  <input type="file" id="filePicker" class="file-picker">
                  <div class="tip-word"><i class="iconfont icon-plus"></i> 请将文件至此或点击上传（全格式）
                  </div>
                </div>
                <div>
                  <ul class="ul-file" style="display: none;"></ul>
                </div>
              </div>
            </div>
          </div>
          <div v-else class="detail-file">

          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Board",
  data() {
    return {
      fileNum: 0,
      showTxt: true,       // default show txt
      textContent: "",
      showText: true,
      dragActive: false
    }
  },
  created() {
  },
  mounted() {
    this.listenerTxt();
    this.listenDragFile()
    // this.listenTextAera();
  },
  methods: {
    listenDragFile() {
      var dropbox = document.getElementById('dragBox')
      dropbox.addEventListener('dragenter', this.onDrag);
      dropbox.addEventListener('dragleave', this.onDragLeave);
      dropbox.addEventListener('drop', this.onDrop);
      // dropbox.addEventListener('dragend', function (){console.log('drag end')});
      dropbox.addEventListener('dragover', this.onDragOver)
    },
    onDrag: function (e) {
      console.log("on drag enter")
      this.dragActive = true;
      e.stopPropagation();
      e.preventDefault();
    },
    onDragOver(e) {
      console.log('drag over');
      e.stopPropagation();
      e.preventDefault();
      this.dragActive = true
    }
    ,
    onDragLeave: function (e) {
      console.log("on leave")
      this.dragActive = false;
      e.stopPropagation();
      e.preventDefault();
    },
    onDrop: function (e) {
      console.log("on drop")
      this.dragActive = false;
      e.stopPropagation();
      e.preventDefault();
      var dt = e.dataTransfer.files;
      console.log(dt);
      // for (var i = 0; i !== dt.files.length; i++) {
      //   // this.uploadFile(dt.files[i]);
      //   console.log(dt.files[i])
      // }
    },
    changeTextFile(event) {
      console.log('switch type');
      this.showText = event;
    }
    ,
    listenerTxt() {
      var container = document.getElementById('textarea');
      var area = container.getElementsByTagName('textarea')[0];
      var span = container.getElementsByTagName('span')[0];
      if (area.addEventListener) {
        area.addEventListener('input', function () {
          span.textContent = area.value;
        }, false);
        span.textContent = area.value;
      } else if (area.attachEvent) {
        area.attachEvent('onpropertychange', function () {
          var html = area.value.replace(/\n/g, '<br/>');
          span.innerText = html;
        });
        var html = area.value.replace(/\n/g, '<br/>');
        span.innerText = html;
      }
      if (window.VBArray && window.addEventListener) { //IE9
        area.attachEvent("onkeydown", function () {
          var key = window.event.keyCode;
          if (key == 8 || key == 46) span.textContent = area.value;

        });
        area.attachEvent("oncut", function () {
          span.textContent = area.value;
        });//处理粘贴
      }
      container.className += "active";

    }
    ,
    listenTextAera() {
      var container = document.getElementById('note-wrapper');
      var aera = document.getElementById('noteContent');
      console.log('aera', aera);
      var preBox = document.getElementById('pre-box');
      console.log('prebox', preBox);
      if (aera.addEventListener) {
        aera.addEventListener('input', function () {
          preBox.textContent = aera.value;
        }, false);
        preBox.textContent = aera.value;
      } else if (aera.attachEvent) {
        aera.attachEvent('onpropertychange', function () {
          var html = aera.value.replace(/n/g, '<br/>');
          preBox.innerText = html;
        });
        var html = aera.value.replace(/n/g, '<br/>');
        preBox.innerText = html;
      }
      if (window.VBArray && window.addEventListener) { //IE9
        aera.attachEvent("onkeydown", function () {
          var key = window.event.keyCode;
          if (key == 8 || key == 46) preBox.textContent = aera.value;

        });
        aera.attachEvent("oncut", function () {
          preBox.textContent = aera.value;
        });//处理粘贴
      }
      container.className += "active";
    }
  }
}
</script>

<style scoped>
.center {
  display: flex;
  align-content: center;
  align-items: center;
}

.container {
  width: 90%;
  height: auto;
  /*background-color: #2c3e50;*/
  /*border-style: groove;*/
  /*min-height: 60vh;*/
  margin: auto;
  margin-top: 6rem;
  display: flex;
  flex-direction: column;
}

.show-box {
  /*background-color: yellow;*/
  width: 100%;
  display: flex;
  flex-direction: column;
  height: auto;
}

.top-box {
  display: flex;
  flex-direction: row;
  height: 4vh;
  font-size: 20px;
  /*border-style: groove;*/
  border-bottom: groove;
}

.button {
  border-style: dotted;
  width: 6rem;
}

.detail-box {
  min-height: 60vh;
  /*margin-bottom: 10vh;*/
}

.detail-txt {
  height: 100%;
  width: 100%;
}

.float-left {
  float: left !important;
}


.note-tab {
  /*margin-top: 15px;*/
  width: 50%;
  /*display: flex;*/
  /*flex-direction: row;*/
  white-space: nowrap;
}

/*
使用 inline-block 后 元素不在一行
说 inline-block 包含换行符，删除源代码换行符依然不行
white-space: nowrap 强制不换行
*/

.note-tab span {
  width: 50%;
  /*height: 100%;*/
  display: inline-block;
  text-align: center;
}

.note-tab span {
  line-height: 40px;
  color: #666;
  height: 40px;
  font-size: 16px;
  padding: 0 20px;
  cursor: pointer;
  /*float: left;*/
  border: 1px solid #bbb;;
  /*white-space: nowrap;*/
}

.note-tab span.active {
  background: #eee;
  border: 1px solid #bbb;
  border-bottom: none;
  color: #000;
}


/************  TEXT area CSS  ********/
textarea, pre {
  margin: 0;
  padding: 0;
  outline: 0;
  border: 0;

}

.expandingArea {
  position: relative;
  border: 1px solid #888;
  background: #fff;
}

.expandingArea textarea,
.expandingArea pre {
  padding: 5px;
  background: transparent;

  /*font: 400 13px/16px helvetica, arial, sans-serif;*/

  font-family: Consolas, "Liberation Mono", Courier, monospace;
  line-height: 1.4;
  font-size: 16px;

  /* Make the text soft-wrap */
  white-space: pre-wrap;
  word-wrap: break-word;
  border: none;
}

.expandingArea textarea {
  font-family: Consolas, "Liberation Mono", Courier, monospace;
  line-height: 1.4;
  font-size: 16px;

  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  -ms-box-sizing: border-box;
  box-sizing: border-box;
  width: 100%;
  /* This height is used when JS is disabled */
  height: 100px;
  border: none;
}

.expandingArea.active textarea {
  /* Hide any scrollbars */
  overflow: hidden;
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  /* Remove WebKit user-resize widget */
  resize: none;
  border: none;
}

.expandingArea pre {
  display: none;
  min-height: 60vh;
}

.expandingArea.active pre {
  display: block;
  /* Hide the text; just using it for sizing */
  visibility: hidden;
}


/* ------------  bote wrapper */

.note-wrapper {
  min-height: 400px;
  height: 100%;
  border: 2px solid #eaeaea;
  position: relative;
}

.note-wrapper pre.pre-box, main .note-box .note-wrapper textarea {
  min-height: 400px;
  font-family: Consolas, "Liberation Mono", Courier, monospace;
  line-height: 1.4;
  font-size: 16px;
  padding: 5px;
  background: transparent;
  white-space: pre-wrap;
  word-wrap: break-word;
  word-spacing: normal;
}

.note-wrapper pre.pre-box {
  visibility: hidden;
  padding-bottom: 50px;
  display: block;
}

@media (max-width: 640px) {
  .note-box .note-wrapper pre.pre-box {
    min-height: 400px;
  }
}

@media (max-width: 640px) {
  .note-box .note-wrapper {
    min-height: 200px;
  }
}

.note-wrapper textarea {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  -ms-box-sizing: border-box;
  box-sizing: border-box;
  width: 100%;
  overflow-y: hidden;
  resize: none;
}

.note-wrapper textarea[readonly] {
  cursor: default;
}

.note-wrapper.file-box {
  padding: 15px 10px;
  min-height: 600px;
  margin-bottom: 15px;
}

@media (max-width: 640px) {
  note-wrapper.file-box {
    min-height: 300px;
  }
}

.note-wrapper.file-box .limit-tip {
  color: #555;
}

.note-wrapper.file-box .limit-tip b {
  color: #00a2ca;
}

.drag-box {
  border: 2px dashed #bbb;
  margin-bottom: 30px;
  border-radius: 5px;
  text-align: center;
  height: 200px;
  font: 20pt bold, "Vollkorn";
  color: #bbb;
  position: relative;
  z-index: 999;
}

.drag-active {
  box-shadow: #42b983;
  border: 3px dashed #bbb;
  background-color: #42b983;
}

@media (max-width: 640px) {
  .note-wrapper.file-box .drag-box {
    height: auto;
    padding: 50px 10px;
  }
}

.note-wrapper.file-box .drag-box .tip-word {
  line-height: 200px;
  text-align: center;
}

.note-wrapper.file-box .drag-box .tip-word i {
  font-size: 30px;
  vertical-align: middle;
}

@media (max-width: 640px) {
  .note-wrapper.file-box .drag-box .tip-word {
    line-height: 40px;
    font-size: 18px;
  }

  .note-wrapper.file-box .drag-box .tip-word i {
    font-size: 20px;
  }
}

.note-wrapper.file-box .drag-box .file-picker {
  position: absolute;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  cursor: pointer;
  opacity: 0;
  filter: alpha(opacity=0);
  user-select: none;
}

.note-wrapper.file-box .download-tip {
  margin-bottom: 15px;
  color: #555;
}

@media (max-width: 640px) {
  .note-wrapper.file-box .download-tip {
    font-size: 12px;
  }
}

.note-wrapper.file-box .table-file {
  font-size: 12px;
}

.note-wrapper.file-box .table-file tr th {
  font-weight: 500;
}


.note-wrapper.file-box .table-file .file-icon {
  color: #555;
  margin-right: 5px;
}

.note-wrapper.file-box .table-file .operate-btn {
  width: 150px;
}

.note-wrapper.file-box .table-file .operate-btn a {
  margin: 0 10px;
}


</style>