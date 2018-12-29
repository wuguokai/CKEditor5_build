## CKEditor5 编译项目

这个项目是本人编译一个CKEditor5项目的实践，如果需要了解其他CKEditor5相关细节，请查看官方文档。
CKEditor5官方文档[地址](https://ckeditor.com/docs/ckeditor5/latest/index.html), CKEditor5官方github[仓库](https://github.com/ckeditor/ckeditor5)

#### 编译步骤：

1. 拉下项目之后，首先使用npm安装依赖：
```
npm install
```
2. 在src下的`ckeditor.js`中添加自己需要的模块和配置，如下：
```javaScript
'use strict';

// The editor creator to use.
import ClassicEditorBase from '@ckeditor/ckeditor5-editor-classic/src/classiceditor';

import EssentialsPlugin from '@ckeditor/ckeditor5-essentials/src/essentials';
import AutoformatPlugin from '@ckeditor/ckeditor5-autoformat/src/autoformat';
import BoldPlugin from '@ckeditor/ckeditor5-basic-styles/src/bold';
import ItalicPlugin from '@ckeditor/ckeditor5-basic-styles/src/italic';
import HeadingPlugin from '@ckeditor/ckeditor5-heading/src/heading';
import LinkPlugin from '@ckeditor/ckeditor5-link/src/link';
import ListPlugin from '@ckeditor/ckeditor5-list/src/list';
import ParagraphPlugin from '@ckeditor/ckeditor5-paragraph/src/paragraph';

import CustomPlugin from 'ckeditor5-custom-package/src/customplugin';  //自定义的插件
import OtherCustomPlugin from '../relative/path/to/some/othercustomplugin'; //其他自定义的插件

export default class ClassicEditor extends ClassicEditorBase {}

// Plugins to include in the build.
ClassicEditor.builtinPlugins = [
    EssentialsPlugin,
    AutoformatPlugin,
    BoldPlugin,
    ItalicPlugin,
    HeadingPlugin,
    LinkPlugin,
    ListPlugin,
    ParagraphPlugin,

    CustomPlugin,  // 添加到插件数组
    OtherCustomPlugin  // 添加到插件数组
];

ClassicEditor.defaultConfig = {
	//添加custombutton到toolbar
    toolbar: [ 'heading', '|', 'bold', 'italic', 'custombutton' ],

    // 这个值需要与 webpack.config.js中的一致。
    language: 'en'
};
```

3. 重新编辑项目：
```
npm run build
```

构建完成之后，你可以在浏览器中打开`sample/index.html`，查看你编译的结果是否正确。