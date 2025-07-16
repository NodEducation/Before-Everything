# 解决GitHub访问问题指南（小白专用）

> 本指南专为技术小白设计，只需按照步骤操作即可解决GitHub访问问题

## 🌟 为什么要做这个操作？

在中国访问GitHub（全球最大的代码托管平台）有时会遇到无法加载的问题。通过修改电脑的**hosts文件**（相当于互联网地址簿），我们可以绕过网络限制，让GitHub网站正常加载。

## 🛠️ 操作步骤（只需5分钟）

### 📝 第一步：复制重要内容
1. 用鼠标**选中**下面灰色框中的所有文字（从`#Github Hosts Start`到`#Github Hosts End`）
2. 按`Ctrl+C`(Windows)或`Command+C`(Mac)复制

```bash
#Github Hosts Start
140.82.113.25 alive.github.com
140.82.114.26 live.github.com
185.199.111.154 github.githubassets.com
140.82.114.22 central.github.com
185.199.110.133 desktop.githubusercontent.com
185.199.110.133 camo.githubusercontent.com
185.199.111.133 github.map.fastly.net
146.75.121.194 github.global.ssl.fastly.net
140.82.121.4 gist.github.com
185.199.109.153 github.io
140.82.121.4 github.com
192.0.66.2 github.blog
140.82.121.5 api.github.com
185.199.111.133 raw.githubusercontent.com
185.199.108.133 user-images.githubusercontent.com
185.199.108.133 favicons.githubusercontent.com
185.199.110.133 avatars5.githubusercontent.com
185.199.111.133 avatars4.githubusercontent.com
185.199.109.133 avatars3.githubusercontent.com
185.199.111.133 avatars2.githubusercontent.com
185.199.111.133 avatars1.githubusercontent.com
185.199.110.133 avatars0.githubusercontent.com
185.199.110.133 avatars.githubusercontent.com
140.82.121.9 codeload.github.com
54.231.197.145 github-cloud.s3.amazonaws.com
3.5.21.193 github-com.s3.amazonaws.com
3.5.24.171 github-production-release-asset-2e65be.s3.amazonaws.com
52.216.48.177 github-production-user-asset-6210df.s3.amazonaws.com
52.217.225.33 github-production-repository-file-5c1aeb.s3.amazonaws.com
185.199.108.153 githubstatus.com
140.82.113.17 github.community
51.137.3.17 github.dev
140.82.113.22 collector.github.com
13.107.42.16 pipelines.actions.githubusercontent.com
185.199.109.133 media.githubusercontent.com
185.199.110.133 cloud.githubusercontent.com
185.199.110.133 objects.githubusercontent.com
#Github Hosts End

```

> ⏰ 最后更新日期：2025年7月5日  

---

### 🖥️ 第二步：修改hosts文件

#### 对于Windows用户：
1. 按`Win键+R`打开运行窗口
2. 输入`notepad`后，**按住`Ctrl+Shift`不放**再按回车（以管理员身份运行）
3. 在记事本中点`文件 > 打开`
4. 粘贴这个路径到地址栏：`C:\Windows\System32\drivers\etc\`
5. 将文件类型改为`所有文件`
6. 选择`hosts`文件并打开
7. 滚动到文件最底部，按`Ctrl+V`粘贴之前复制的内容
8. 按`Ctrl+S`保存

> 💡 如果无法保存：请确保你是用管理员身份打开的记事本

#### 对于Mac用户：
1. 打开`应用程序 > 实用工具 > 终端`
2. 输入：`sudo nano /etc/hosts` 后按回车
3. 输入电脑密码（输入时不会显示字符，输完直接回车）
4. 用方向键滚动到文件底部
5. 按`Command+V`粘贴内容
6. 按`Control+O`保存 → 回车确认 → 按`Control+X`退出

#### 对于Linux用户：
1. 打开终端
2. 输入：`sudo gedit /etc/hosts`（Ubuntu）或`sudo nano /etc/hosts`（其他版本）
3. 输入密码后回车
4. 滚动到文件底部粘贴内容
5. 保存并关闭

---

### ⚡ 第三步：刷新网络设置

#### Windows用户：
1. 按`Win键+R`打开运行窗口
2. 输入`cmd`后回车
3. 在黑色窗口输入：`ipconfig /flushdns`
4. 看到"成功刷新DNS解析缓存"提示即可

#### Mac用户：
1. 打开终端
2. 输入：`sudo killall -HUP mDNSResponder`
3. 输入密码后回车（无提示）

#### Linux用户：
1. 打开终端
2. 输入：`sudo nscd restart`或`sudo systemctl restart systemd-resolved`

> 🔄 如果以上操作后仍无法访问，请**重启电脑**后再试

---

## ❓ 常见问题解答

### Q：这个操作安全吗？
A：完全安全！只是添加了GitHub的官方服务器地址，不会影响其他网站

### Q：操作后需要还原吗？
A：不需要！这些设置会长期有效。如果未来GitHub访问又出问题，可能需要更新hosts内容

### Q：为什么我保存hosts文件时被拒绝？
A：因为你没有管理员权限。请严格按照第二步的"管理员身份运行"操作

### Q：修改后还能正常访问其他网站吗？
A：完全不影响！这个修改只针对GitHub相关网站

---

写在最后，如果上述的方案不能满足你的要求，而你又是 Windows系统

- 访问 [host文件下载](https://raw.hellogithub.com/hosts) 得到最新的 hosts文件

- 打开本地文件目录 `C:\Windows\System32\drivers\etc`，将下载的hosts文件放在目录里（如原本有文件则进行替换，若没有hosts文件就直接复制即可）

- 刷新本机DNS后再次尝试登录Github

