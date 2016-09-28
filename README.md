URLRedirector
=============

使用 WebExtension 方式编写的 Firefox URL 重定向插件。

插件的开发受 [gooreplacer](https://github.com/jiacai2050/gooreplacer) 启发，由于 gooreplacer 在 MAC 下运行时会遇到停止运行的问题，因此换成 WebExtension 方式实现。

插件仅支持正则表达式替换方式，不支持通配符。

版本和特性列表
-------

目前支持的特性：

1. 支持在线规则、在线规则自动更新
2. 支持自定义规则

限于 WebExtension 的能力，目前不支持导入、导出配置。

其它说明
----

内部规则 Rule 为简单 javascript 对象：

    {
        origin: <原始地址>,
        target: <目标地址>,
        enable: <是否启用>
    }

在线规则使用一个包含了规则列表的 json 格式的文件表示：

    {
        version: <版本号，可选>,
        rules: <规则列表，必须>
    }

目前支持两种格式，通过 version 进行区分。
（1）不包含 version 或 version < 1.0 时，使用 gooreplacer 定义的格式，见 `tools/gooreplacer.gson` 或 [在线规则](https://github.com/jiacai2050/gooreplacer4chrome/raw/master/gooreplacer.gson) ；
（2）包含 version 且 version >= 1.0 时，使用新格式，见 `tools/rules.json` 。

两种格式的主要区别在于 rules 字段，在 gooreplacer 中 rules 为对象，在新格式中，rules 为列表。

License
-------

Copyright © 2016 Yingcai FENG

The MIT License (MIT)

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the “Software”), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
