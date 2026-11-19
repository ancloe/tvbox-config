影视仓 Python 点播源配置包

目录结构（部署时必须保持不变）：
  box.json
  py/
    sotvla.py
    souju_ai.py
    shijue_yingshi.py
    sudugu.py
    shouying.py
    shiliu_duanju.py
    shuabu_ting_duanju.py
    shouji_yingyuan.py

配置说明：
- box.json 中 8 个站点均为 type=3 Python Spider。
- api 使用 ./py/xxx.py 相对路径；路径相对于 box.json 所在目录。
- Python 文件输出 Spider 类，并继承 base.spider.Spider。
- 本包只收录普通影视和短剧脚本；没有收录压缩包中的成人内容脚本。

检查结果：
- 8 个 Python 文件均通过 Python AST 语法解析。
- box.json 可正常解析，8 个站点的 api 路径均能对应到实际文件。
- 这不代表已经在影视仓设备上完成运行或播放测试；各资源站的域名、网页结构、访问限制可能变化。

依赖提醒：
- 多个脚本使用 requests。
- sudugu.py、shuabu_ting_duanju.py 使用 beautifulsoup4（bs4）。
- sotvla.py、shijue_yingshi.py 使用 lxml。
- 个别脚本会用到 urllib3。
- 影视仓需支持 Python Spider，并安装与应用版本及设备 ABI 匹配的 Python 模块；运行模块还需提供脚本所需第三方库，否则个别源可能加载失败。

GitHub Pages 部署（免费静态托管）：
1. 登录 GitHub，新建一个 Public 仓库，例如 tvbox-config。
2. 解压本 ZIP，把 box.json 和整个 py 文件夹上传到仓库根目录（不要只上传 box.json）。
3. 进入仓库 Settings → Pages。
4. 在 Build and deployment 中选择 Deploy from a branch；Branch 选 main，目录选 /(root)，保存。
5. 等待 GitHub Pages 发布完成。配置链接格式为：
   https://你的GitHub用户名.github.io/tvbox-config/box.json
6. 把该链接添加到影视仓的配置/订阅地址中。

如果仓库名不是 tvbox-config，链接中的仓库名也要相应替换。
