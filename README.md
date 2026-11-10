# dsh-purge 1.1.56 + DSH 0.1.7-rc.2

本仓库是 [mmparko/dsh-purge](https://github.com/mmparko/dsh-purge) 的私有副本（该仓库本身又是已删库的
[YuJunZhiXue/dsh-purge](https://github.com/YuJunZhiXue/dsh-purge) 的全量镜像）。
原始 README 已改名为 [README.upstream.md](README.upstream.md)。

| 项 | 内容 |
| --- | --- |
| 仓库地址 | [github.com/zhaoyy0513/dsh-purge](https://github.com/zhaoyy0513/dsh-purge) |
| 插件版本 | `v1.1.56`（另含 `v1.1.34` 等全部历史版本 tag） |
| 宿主版本 | DeepSeek Harness `0.1.7-rc.2` |

> `0.1.7rc2` 指的是 **DSH 宿主（DeepSeek Harness）**的版本，不是 dsh-purge 插件的版本。
> 社区推荐的组合是 **DSH 0.1.7rc2 + dsh-purge 1.1.34 或 1.1.56**。

---

## 一、安装 DSH 宿主 0.1.7-rc.2

```sh
npm i -g @deepseek-ai/dsh@0.1.7-rc.2
```

验证：

```sh
dsh --version
```

---

## 二、安装 dsh-purge 1.1.56

**Web（官方 `dsh web`）**

```sh
dsh plugin --profile web add dsh-purge
```

**桌面版（官方 EXE）**

```sh
dsh plugin --profile desktop add dsh-purge
```

npm 源不可用时，可改用 tarball：

```sh
dsh plugin --profile web add https://github.com/zhaoyy0513/dsh-purge/archive/refs/tags/v1.1.56.tar.gz
```

---

## 三、使用步骤（Web / 桌面各做一次）

1. **完全退出并重启** 你安装进去的那个宿主：重启 `dsh web`，或退出桌面托盘再重新打开 EXE。
2. 在**该宿主**上，点会话标题旁的 **dsh-purge**，然后在 **Clean** 页点 **Apply**。（它不在宿主设置页里）
3. 一次成功的 **Apply** 会重启一次以加载补丁；没完成则不会重启。

> Web 的控制只影响 Web，桌面的控制只影响桌面端，不要跨宿主 Apply。

### 如何确认安装成功

- 会话标题旁出现 **dsh-purge**，Clean 页有 **Apply**。
- 在对话里输入 `/purge status`，会打印 `DSH_HOME` 和补丁列表。
- 未安装的可选包会显示为 skipped，不影响 Apply。

---

## 四、卸载

**dsh-purge** → **Clean** → **Uninstall**，确认即可（还原补丁、恢复原始 Harness 并重启当前宿主）。

```sh
dsh-purge --uninstall
# 或 /purge uninstall
```

---

## 五、版本说明

| 版本 | 说明 |
| --- | --- |
| `v1.1.34` | 知识库列出本机模板，更新包在三端都能解压 |
| `v1.1.56` | 空框不再写入默认提示词 |
| `v1.1.71` | 镜像收录的最新版本 |

> 本仓库已同步上游全部分支与全部 tag（含 `archive/pr-*` PR 归档 tag），并配置了每天自动同步上游变更。
