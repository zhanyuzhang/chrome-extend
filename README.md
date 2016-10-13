# chrome-extend
### Chrome扩展的工程结构
一般的扩展工程包括：
```
      -- icon.png（扩展的图标）
      -- background.js（背景页的js文件，后台运行）
      -- content_script.js（web页面内运行的js文件，可访问页面的DOM）
      -- popup.html（用户点击扩展图标弹出的html文件）
      -- mainfest.json（配置文件）
```

### mainfest.json文件
```json
{
  "manifest_version": 2,    #必须为2
  "name": "扩展名称",
  "description": "扩展描述",
  "version": "1.0",
  "icons": {     #扩展程序页的扩展图标
    "16": "icon16.png",
    "48": "icon48.png",
    "128": "icon128.png"},
  "browser_action": {
    "default_icon": {     #浏览器地址栏的扩展图标
      "19": "icon19.png",
      "38": "icon38.png"},
    "default_popup": "popup.html",
    "default_title": "标题"},
  "background":{
    "scripts":["background.js"]
  },
  "content_scripts": [{  
       "matches": ["http://*/*","https://*/*"],  #向哪些页面注入js
       "js": ["content_scirpt.js"],   
       "run_at": "document_idle",  #content_scirpt.js注入的时间
       "all_frames": true}],  
  "permissions": [      #扩展程序的权限
    "cookies",
    "notifications",
    "idle",
    "http://*/",
    "https://*/"
  ]
}
```

### Demo
chrome_shieldBaiDu 扩展的作用是屏蔽百度推广
chrome_hack 扩展主要是关于窃取用户账号密码的恶意插件的一个demo chrome_hack中的data.php为后台文件

### 安装方式：
```
1.地址栏输入chrome://extensions/ ,进入到扩展程序页；
2.选择“加载已解压的扩展程序”。
```
