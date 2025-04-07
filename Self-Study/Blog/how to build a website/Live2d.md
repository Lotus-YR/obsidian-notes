# Live2D简介
Live2D 是一种**二维动画技术**，可以让静态的二维角色或图像进行动态表现，类似于三维动画，但保持二维风格。它通过对二维图像进行分层，并使用骨骼动画技术使这些层次独立运动，从而使角色看起来像是“活”起来了。与传统的二维动画相比，Live2D 能够保留艺术风格的同时，通过简单的动画效果创造出非常流畅和自然的运动效果。

# 使用方法
在 Hexo 博客中使用 Live2D 主要是通过嵌入 Live2D 模型，并在页面中设置相关的 JavaScript 代码和样式。

安装hexo插件：
`npm install -save hexo-helper-live2d`

_ config.yml中修改配置
```
live2d:
  enable: true
  scriptFrom: local
  pluginRootPath: live2dw/
  pluginJsPath: lib/
  pluginModelPath: assets/
  tagMode: false
  log: false
  model:
    use: live2d-widget-model-<你喜欢的模型名字>
  display:
    position: right
    width: 150
    height: 300
  mobile:
    show: true
```

下载模型的相关文件：
`npm install --save live2d-widget-model-<模型名字>`

可供选择模型：
live2d-widget-model-chitose
live2d-widget-model-epsilon2_1
live2d-widget-model-gf
live2d-widget-model-haru/01 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haru/02 (use npm install --save live2d-widget-model-haru)
live2d-widget-model-haruto
live2d-widget-model-hibiki
live2d-widget-model-hijiki （黑猫）
live2d-widget-model-izumi
live2d-widget-model-koharu
live2d-widget-model-miku
live2d-widget-model-ni-j
live2d-widget-model-nico
live2d-widget-model-nietzsche
live2d-widget-model-nipsilon
live2d-widget-model-nito
live2d-widget-model-shizuku
live2d-widget-model-tororo （白猫）
live2d-widget-model-tsumiki
live2d-widget-model-unitychan
live2d-widget-model-wanko （茶杯小狗）
live2d-widget-model-z16

