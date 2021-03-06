# why need config

Cocos website exists:

1. English: `http://www.cocos2d-x.org/`
1. 中文：`http://www.cocos.com/`

the gitbook be published twice, links are different on both. So add the config to adapt this.

## how to change

Config of the master branch will be for cocos.com, if you need to change config to cocos2d-x.org, only need run:

```sh
cd to docs root dir
> cp -rf config/cocos2d-x.org/ ./
```

## What has been changed?

1. 添加了手册文档， Api 文档的版本切换功能。<br>(Add a new feature switch the version of tutorial docs and Api docs.)
2. 修改了 css 样式，用于新功能的动态布局。<br>(Modify the css code in order to dynamic adaptate the layout.)
3. en 文件夹下的 book.json 增加新数组记录新版本链接和名称。<br>(Add a new array in book.json which exist in en(zh) fold, the array use to record the new doc version link and name.)
4. page.html 和 header.html 模板修改，增加关于切换版本的内容。<br>(Modify the template html files, increase a part of code to relate to the new feature.)

## How to change your official website content?

1. 实际上大部分的内容已经上传到主仓库：https://github.com/cocos-creator/creator-docs <br> 你需要将最新的提交 pull 到本地。之后执行 cp 命令将旧的文件进行覆盖。
   __请记得将中文网站的官网链接替换为英文网站的链接__
2. 接下来需要你关注 book.json 这个文件，它 __存在于 en / zh 文件夹__ 下，查看内容你会发现如下图 1-1 所示：
![1-1](![image](https://user-images.githubusercontent.com/35832931/43818599-ed067654-9b11-11e8-84ad-913e332c77f3.png))

    上图中有三个版本的手册内容，分别包含 __名称__ 以及 __链接__ 参数。__每当你发布一个新的版本手册时，都需要将对应的手册名称，链接添加到这个 book.json 中。__
    __请记住： 链接（link）的对应格式 :__
    ```
    // this is the creator docs format
    official_path/version_number/manual/language

    // this is the creator api docs format
    official_path/version_number/api/language
    ```
    因为不同版本间文档并不是公用一套 book.json 内容（这意味着多份 book.json 文件），所以在这里提醒一下，一旦修改了一个版本下的 book.json, 其他版本下的 book.json 文件一样需要修改。

3. 创建你自己的版本内容，首先每一个版本的手册都需要你创建一个对应的本地文件库（不同版本间的文档内容是相互独立的），根据不同的版本手册内容执行 gitbook install 安装插件，之后执行 gitbook 的构建命令生成对应的 _book。
4. 最后发布，将对应的版本手册库放入自己制定的发布文件夹（这个文件夹的位置决定了你的链接地址）下，并且记得将 book.json 中对应的链接修改成为你安放库的路径。