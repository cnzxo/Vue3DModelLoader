<!--

////////////////////////////////////////////////////////////////////
//                          _ooOoo_                               //
//                         o8888888o                              //
//                         88" . "88                              //
//                         (| ^_^ |)                              //
//                         O\  =  /O                              //
//                      ____/`---'\____                           //
//                    .'  \\|     |//  `.                         //
//                   /  \\|||  :  |||//  \                        //
//                  /  _||||| -:- |||||-  \                       //
//                  |   | \\\  -  /// |   |                       //
//                  | \_|  ''\---/''  |   |                       //
//                  \  .-\__  `-`  ___/-. /                       //
//                ___`. .'  /--.--\  `. . ___                     //
//              ."" '<  `.___\_<|>_/___.'  >'"".                  //
//            | | :  `- \`.;`\ _ /`;.`/ - ` : | |                 //
//            \  \ `-.   \_ __\ /__ _/   .-` /  /                 //
//      ========`-.____`-.___\_____/___.-`____.-'========         //
//                           `=---='                              //
//      ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^        //
//              佛祖保佑       永无BUG     永不修改                   //
////////////////////////////////////////////////////////////////////

-->
<template>
  <!-- 加载器 -->
  <div class="loader">
    <!-- 模型 -->
    <div class="model">
      <!-- 模型信息 -->
      <div class="model-information" v-if="isShowModelInformation">
        <table class="model-information-table">
          <thead>
          <tr>
            <th>ID</th>
            <th>Key</th>
            <th>Value</th>
          </tr>
          </thead>
          <tbody>
          <tr>
            <td>1</td>
            <td>ModelUrl</td>
            <td>{{ model.url }}</td>
          </tr>
          <tr>
            <td>2</td>
            <td>ModelType</td>
            <td>{{ model.type }}</td>
          </tr>
          </tbody>
        </table>
      </div>
      <!-- 模型展示 -->
      <div class="model-title">3D Model</div>
      <div :class="modelClass" v-if="isShowModel" ref="full-screen">
        <!-- .obj -->
        <div class="controls-buttons">
          <img :src="fullScreenIcon" class="full-screen-button" @click="onFullScreen"
               alt="vue-3d-model-loader"/>
        </div>
        <model-obj class="model-item" v-if="model.type==='obj'"
                   :src="model.url"
                   :position="model.position"
                   :rotation="model.rotation"
                   :cameraPosition="model.cameraPosition"
                   :cameraRotation="model.cameraRotation"
                   :scale="model.scale"
                   :lights="model.lights"
                   :backgroundColor="model.backgroundColor"
                   :backgroundAlpha="model.backgroundAlpha"
                   :controlsOptions="model.controlsOptions"
                   :crossOrigin="model.crossOrigin"
                   @on-load="onLoad"
                   @on-progress="updateProgressBar"
        ></model-obj>
        <!-- .stl -->
        <model-stl v-if="model.type==='stl'"
                   :src="model.url"
                   :position="model.position"
                   :rotation="model.rotation"
                   :cameraPosition="model.cameraPosition"
                   :cameraRotation="model.cameraRotation"
                   :scale="model.scale"
                   :lights="model.lights"
                   :backgroundColor="model.backgroundColor"
                   :backgroundAlpha="model.backgroundAlpha"
                   :controlsOptions="model.controlsOptions"
                   :crossOrigin="model.crossOrigin"
                   @on-load="onLoad"
                   @on-progress="updateProgressBar"
        ></model-stl>
        <!-- .dae -->
        <model-collada v-if="model.type==='dae'"
                       :src="model.url"
                       :position="model.position"
                       :rotation="model.rotation"
                       :cameraPosition="model.cameraPosition"
                       :cameraRotation="model.cameraRotation"
                       :scale="model.scale"
                       :lights="model.lights"
                       :backgroundColor="model.backgroundColor"
                       :backgroundAlpha="model.backgroundAlpha"
                       :controlsOptions="model.controlsOptions"
                       :crossOrigin="model.crossOrigin"
                       @on-load="onLoad"
                       @on-progress="updateProgressBar"
        ></model-collada>
        <!-- .json -->
        <model-three v-if="model.type==='json'"
                     :src="model.url"
                     :position="model.position"
                     :rotation="model.rotation"
                     :cameraPosition="model.cameraPosition"
                     :cameraRotation="model.cameraRotation"
                     :scale="model.scale"
                     :lights="model.lights"
                     :backgroundColor="model.backgroundColor"
                     :backgroundAlpha="model.backgroundAlpha"
                     :controlsOptions="model.controlsOptions"
                     :crossOrigin="model.crossOrigin"
                     @on-load="onLoad"
                     @on-progress="updateProgressBar"
        ></model-three>
        <!-- .ply -->
        <model-ply v-if="model.type==='ply'"
                   :src="model.url"
                   :position="model.position"
                   :rotation="model.rotation"
                   :cameraPosition="model.cameraPosition"
                   :cameraRotation="model.cameraRotation"
                   :scale="model.scale"
                   :lights="model.lights"
                   :backgroundColor="model.backgroundColor"
                   :backgroundAlpha="model.backgroundAlpha"
                   :controlsOptions="model.controlsOptions"
                   :crossOrigin="model.crossOrigin"
                   @on-load="onLoad"
                   @on-progress="updateProgressBar"
        ></model-ply>
        <!-- .fbx -->
        <model-fbx v-if="model.type==='fbx'"
                   :src="model.url"
                   :position="model.position"
                   :rotation="model.rotation"
                   :cameraPosition="model.cameraPosition"
                   :cameraRotation="model.cameraRotation"
                   :scale="model.scale"
                   :lights="model.lights"
                   :backgroundColor="model.backgroundColor"
                   :backgroundAlpha="model.backgroundAlpha"
                   :controlsOptions="model.controlsOptions"
                   :crossOrigin="model.crossOrigin"
                   @on-load="onLoad"
                   @on-progress="updateProgressBar"
        ></model-fbx>
        <!-- .gltf -->
        <model-gltf v-if="model.type==='gltf'"
                    :src="model.url"
                    :position="model.position"
                    :rotation="model.rotation"
                    :cameraPosition="model.cameraPosition"
                    :cameraRotation="model.cameraRotation"
                    :scale="model.scale"
                    :lights="model.lights"
                    :backgroundColor="model.backgroundColor"
                    :backgroundAlpha="model.backgroundAlpha"
                    :controlsOptions="model.controlsOptions"
                    :crossOrigin="model.crossOrigin"
                    @on-load="onLoad"
                    @on-progress="updateProgressBar"
        ></model-gltf>
      </div>
      <!-- 加载进度条 -->
      <div class="model-progress" v-show="isShowLoadProgress">
        <!-- 进度条配置-->
        <progress-bar :val="progress.currentValue"
                      :max="progress.maxValue"
                      :size="progress.barSize"
                      :text="progress.barText"
                      :text-align="progress.barTextAlign"
                      :text-fg-color="progress.barTextColor"
                      :text-position="progress.barTextPosition"
                      :font-size="progress.barFontSize"
                      :bar-color="progress.barColor"
                      :bg-color="progress.barBackgroundColor"
                      :bar-transition="progress.barTransition"
                      :bar-border-radius="progress.barBorderRadius"
                      :spacing="progress.barSpacing"
        ></progress-bar>
        <!-- 进度条底部文本 -->
        <div class="model-progress-text"
             :style="{'color':progress.bottomTextColor,'font-size':progress.bottomFontSize}">
          <p>{{ progress.bottomText }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>

//
//                                                 .:::::::::::::::::.
//                       .::::.                   ::                 ::
//                     .::::::::.                 ::   年轻人不讲武德！ ::
//                    :::::::::::                .::                 ::
//                 ..:::::::::::'              .:::::::::::::::::::::'
//              '::::::::::::'
//                .::::::::::
//           '::::::::::::::..
//                ..::::::::::::.
//              ``::::::::::::::::
//               ::::``:::::::::'        .:::.
//              ::::'   ':::::'       .::::::::.
//            .::::'      ::::     .:::::::'::::.
//           .:::'       :::::  .:::::::::' ':::::.
//          .::'        :::::.:::::::::'      ':::::.
//         .::'         ::::::::::::::'         ``::::.
//     ...:::           ::::::::::::'              ``::.
//    ```` ':.          ':::::::::'                  ::::..
//                       '.:::::'                    ':'````..
//
//
/////////////////////////////////////////////////////////////////////////
//                                                                     //
//  参考文献：https://hujiulong.github.io/vue-3d-model                   //
//                                                                     //
/////////////////////////////////////////////////////////////////////////

import {ModelObj} from 'vue-3d-model'
import {ModelStl} from 'vue-3d-model'
import {ModelCollada} from 'vue-3d-model'
import {ModelThree} from 'vue-3d-model'
import {ModelFbx} from 'vue-3d-model'
import {ModelPly} from 'vue-3d-model'
import {ModelGltf} from 'vue-3d-model'
import ProgressBar from 'vue-simple-progress'

export default {
  name: 'Vue3DModelLoader',
  props: {
    url: String,    // 模型文件路径
    showModel: Boolean,    // 是否显示模型
    showMessage: Boolean,    // 是否显示消息
    showProgress: Boolean,   // 是否显示进度条
    modelConfig: Object,   // 模型配置信息
    progressConfig: Object,    // 进度条配置信息
    rotateModel: Boolean,    // 旋转模型
    rotateConfig: Object,    // 旋转相关配置
  },
  components: {
    ModelObj,
    ModelStl,
    ModelCollada,
    ModelThree,
    ModelFbx,
    ModelPly,
    ModelGltf,
    ProgressBar,
  },
  data() {
    return {
      fullScreenIcon: '/static/images/full_screen.png',
      modelClass: 'model-display',
      isFullScreen: false,
      // 模型配置
      model: {
        url: this.url,    // 模型文件路径，可以是本地文件，也可以是远程文件
        type: null,   // 模型文件类型，自动识别文件类型，无需手动指定
        position: {   // 模型定位
          x: 0,
          y: 0,
          z: 0,
        },
        rotation: {   // 旋转模型
          x: 0,
          y: 0,
          z: 0,
        },
        cameraPosition: {   // 相机定位
          x: 0,
          y: 0,
          z: 0,
        },
        cameraRotation: {   // 相机旋转
          x: 0,
          y: 0,
          z: 0,
        },
        scale: {    // 规模
          x: 1,
          y: 1,
          z: 1,
        },
        lights: [   // 灯光
          {
            type: 'DirectionalLight',   // 灯光类型
            position: {   // 灯光位置
              x: 1,
              y: 1,
              z: 0,
            },
            color: 0xffffff,
            intensity: 0.8
          }, {
            type: 'DirectionalLight',   // 灯光类型
            position: {   // 灯光位置
              x: -1,
              y: -1,
              z: 0,
            },
            color: 0xffffff,
            intensity: 0.8
          },
        ],
        backgroundColor: '#000',    // 模型背景颜色
        backgroundAlpha: 1,    // 透明度（0-1）
        controlsOptions: {},    // 控制选项
        crossOrigin: 'anonymous',   // 跨域请求
        glOptions: {    // 系统参数
          antialias: true,
          alpha: true
        },
      },
      isShowModelInformation: false,     // 是否显示模型信息
      isShowLoadProgress: false,   // 是否显示加载进度条
      isShowModel: true,   // 是否显示模型
      isRotateModel: false,    // 是否旋转模型
      // 进度条默认配置
      progress: {
        currentValue: 0,   // 当前已加载
        maxValue: 100,    // 最大值
        barSize: 'large',    // 进度条大小  例如：tiny, small, medium, large, huge, massive, {n}
        barColor: '#4693dc',    // 进度条颜色
        barText: '',   // 进度条文本内容
        barTextColor: '#fff',   // 进度条文本颜色
        barTextAlign: 'right',   // 进度条文本对齐方式
        barTextPosition: 'inside',   // 进度条文本位置  例如：bottom, top, middle, inside
        barFontSize: 13,    // 进度条字体大小
        barTransition: 'all 0.5s ease',   // 进度条过渡时间
        barBorderRadius: 0,   // 进度条圆角大小
        barBackgroundColor: '#eee',    // 进度条背景颜色
        bottomText: 'loading...',   // 底部文本内容
        bottomTextColor: '#000',    // 底部文本颜色
        bottomFinishText: 'loaded',   // 加载完成显示文本
        bottomFontSize: 13,    // 底部字体大小
        barSpacing: 4,   // 进度条内部空间
      },
      // 旋转默认配置
      rotate: {
        x: {
          speed: 0,   // 沿X轴旋转速度
        },
        y: {
          speed: 0,    // 沿Y轴旋转速度
        },
        z: {
          speed: 0,   // 沿Z轴旋转速度
        },
      },
      modelConfigData: {},    // 模型配置数据
      progressConfigData: {},   // 进度条配置数据
      rotateConfigData: {},    // 旋转配置数据
    }
  },
  mounted() {
    // 是否显示模型
    this.isShowModel = this.showModel;
    // 是否显示消息
    this.isShowModelInformation = this.showMessage;
    // 是否显示进度条
    this.isShowLoadProgress = this.showProgress;
    // 是否旋转模型
    this.isRotateModel = this.rotateModel;
    // 获取模型文件类型
    this.model.type = this.getModelFileType();
    // 获取模型配置数据
    this.modelConfigData = this.modelConfig ? this.modelConfig : {};
    // 设置模型配置信息
    this.setModelConfig();
    // 获取进度条配置，若未配置，则初始化为空对象，防止报错
    this.progressConfigData = this.progressConfig ? this.progressConfig : {};
    // 设置进度条配置信息
    this.setProgressConfig();
    // 获取旋转配置
    this.rotateConfigData = this.rotateConfig ? this.rotateConfig : {};
    // 设置旋转配置信息
    this.setRotateConfig();
  },
  methods: {
    /**
     * 初始化
     **/
    onLoad() {
      if (this.isRotateModel) {
        // 开始旋转
        this.startRotateModel();
      }
    },

    /**
     * 旋转模型
     */
    startRotateModel() {
      this.model.rotation.x += this.rotate.x.speed;
      this.model.rotation.y += this.rotate.y.speed;
      this.model.rotation.z += this.rotate.z.speed;
      requestAnimationFrame(this.startRotateModel);
    },

    /**
     *  设置旋转配置
     */
    setRotateConfig() {
      // 获取旋转配置信息
      let config = this.rotateConfigData;
      if (('x' in config)) {
        this.rotate.x.speed = config.x.speed;
      }
      if (('y' in config)) {
        this.rotate.y.speed = config.y.speed;
      }
      if (('z' in config)) {
        this.rotate.z.speed = config.z.speed;
      }
    },

    /**
     * 获取模型文件类型
     * @returns {*} 模型文件类型字符串
     */
    getModelFileType() {
      // 获取模型文件路径
      let modelFileUrl = this.model.url;
      // 模型文件类型变量定义
      let modelFileType = null;
      // 拆分文件路径字符串
      try {
        // 以“.”为分隔符对字符串进行拆分
        let modelUrlArray = modelFileUrl.split('.');
        // 获取拆分结果数组的最后一个元素的索引
        let modelUrlArrayLastIndex = modelUrlArray.length - 1;
        // 获取拆分结果数组的最后一个元素值
        modelFileType = modelUrlArray[modelUrlArrayLastIndex];
      } catch (error) {   // 拆分失败处理相关
        modelFileType = null;
        console.log(error);
      }
      // 返回模型文件类型字符串
      return modelFileType;
    },

    /**
     * 设置模型配置信息
     **/
    setModelConfig() {
      // 获取模型配置信息
      let config = this.modelConfigData;
      if (('position' in config)) {
        this.model.position = config.position;
      }
      if (('rotation' in config)) {
        this.model.rotation = config.rotation;
      }
      if (('cameraPosition' in config)) {
        this.model.cameraPosition = config.cameraPosition;
      }
      if (('cameraRotation' in config)) {
        this.model.cameraRotation = config.cameraRotation;
      }
      if (('scale' in config)) {
        this.model.scale = config.scale;
      }
      if (('lights' in config)) {
        this.model.lights = config.lights;
      }
      if (('backgroundColor' in config)) {
        this.model.backgroundColor = config.backgroundColor;
      }
      if (('backgroundAlpha' in config)) {
        this.model.backgroundAlpha = config.backgroundAlpha;
      }
      if (('controlsOptions' in config)) {
        this.model.controlsOptions = config.controlsOptions;
      }
      if (('crossOrigin' in config)) {
        this.model.crossOrigin = config.crossOrigin;
      }
    },

    /**
     * 设置进度条配置
     */
    setProgressConfig() {
      // 获取进度条配置信息
      let config = this.progressConfigData;
      if (('barSize' in config)) {
        this.progress.barSize = config.barSize;
      }
      if (('barColor' in config)) {
        this.progress.barColor = config.barColor;
      }
      if (('barText' in config)) {
        this.progress.barText = config.barText;
      }
      if (('barTextColor' in config)) {
        this.progress.barTextColor = config.barTextColor;
      }
      if (('barTextAlign' in config)) {
        this.progress.barTextAlign = config.barTextAlign;
      }
      if (('barTextPosition' in config)) {
        this.progress.barTextPosition = config.barTextPosition;
      }
      if (('barFontSize' in config)) {
        this.progress.barFontSize = config.barFontSize;
      }
      if (('barTransition' in config)) {
        this.progress.barTransition = config.barTransition;
      }
      if (('barBorderRadius' in config)) {
        this.progress.barBorderRadius = config.barBorderRadius;
      }
      if (('barBackgroundColor' in config)) {
        this.progress.barBackgroundColor = config.barBackgroundColor;
      }
      if (('bottomText' in config)) {
        this.progress.bottomText = config.bottomText;
      }
      if (('bottomTextColor' in config)) {
        this.progress.bottomTextColor = config.bottomTextColor;
      }
      if (('bottomFinishText' in config)) {
        this.progress.bottomFinishText = config.bottomFinishText;
      }
      if (('bottomFontSize' in config)) {
        this.progress.bottomFontSize = config.bottomFontSize;
      }
      if (('barSpacing' in config)) {
        this.progress.barSpacing = config.barSpacing;
      }
    },

    /**
     * 更新进度条信息
     * @param e
     */
    updateProgressBar(e) {
      // 获取当前加载进度
      let currentValue = e.loaded;
      // 获取总大小
      let maxValue = e.total;
      // 设置当前进度
      this.progress.currentValue = currentValue;
      // 设置总大小
      this.progress.maxValue = maxValue;
      // 求当前进度值与总大小的商
      let quotientValue = currentValue / maxValue;
      // 对商向下取整，再扩乘以100
      let roundingValue = Math.floor(quotientValue * 100);
      // 设置加载完成相关
      if (roundingValue === 100) {
        // 设置底部加载完成文本
        this.progress.bottomText = this.progress.bottomFinishText;
        // 延时1s执行
        let that = this;
        setTimeout(function () {
          // 关闭进度条
          that.isShowLoadProgress = false;
        }, 1000);
      }
      // 获取百分比
      let percentageValue = roundingValue.toString() + '%';
      // 设置进度条文本显示内容
      this.progress.barText = percentageValue;
      // 控制台显示进度
      console.log(percentageValue);
    },

    /**
     * 全屏相关
     */
    onFullScreen() {
      // 是否开启全屏
      if (this.isFullScreen) {
        console.log('开启全屏')
        this.isFullScreen = false;
        this.closeFullScreen();
      } else {
        console.log('关闭全屏');
        this.isFullScreen = true;
        this.openFullScreen();
      }
    },

    /**
     * 开启全屏
     */
    openFullScreen() {
      this.modelClass = 'model-display full-screen-active';
      this.fullScreenIcon = '/static/images/full_screen_exit.png';
    },

    /**
     * 关闭全屏
     */
    closeFullScreen() {
      this.modelClass = 'model-display';
      this.fullScreenIcon = '/static/images/full_screen.png';
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.model-information-table {
  width: calc(100% + 4px);
  margin: -2px;
}

.model-information-table tr {
  line-height: 50px;
}

.model-information-table thead > tr {
  color: #fff;
  background: #4693dc;
}

.model-information-table tbody > tr {
  color: #000;
  background: #f1f1f1;
}

.model-information-table td {
  padding: 10px;
}

.model-information-table tr > td:first-child {
  text-align: center;
}

.model-display {
  position: relative;
  margin-bottom: 10px;
}

.model-item {
  background: #000;
}

.full-screen-active {
  width: 100%;
  height: 100%;
  position: fixed;
  top: 0;
  left: 0;
}

.model-title {
  height: 40px;
  color: white;
  display: flex;
  align-items: center;
  padding-left: 10px;
  background: #008b8b;
}

.model-progress-text {
  text-align: center;
}

.controls-buttons {
  position: absolute;
  bottom: 0;
  right: 2px;
}

.full-screen-button {
  width: 30px;
  height: 30px;
}

.full-screen-button:hover {
  cursor: pointer;
}
</style>
