# Fork 同步备忘

本仓库是 [datawhalechina/jev-cookbook](https://github.com/datawhalechina/jev-cookbook) 的 fork。自己的修改推到 `origin`，原仓库的更新从 `upstream` 拉取。

| 远程 | 仓库 | 用途 |
| --- | --- | --- |
| `origin` | https://github.com/junfuhuang/jev-cookbook.git | 自己的修改，往这里推 |
| `upstream` | https://github.com/datawhalechina/jev-cookbook.git | 只拉取。push URL 已设为 `DISABLE`，避免误推到原仓库 |

当前远程可用下面命令核对：

```bash
git remote -v
```

预期输出：

```text
origin    https://github.com/junfuhuang/jev-cookbook.git (fetch)
origin    https://github.com/junfuhuang/jev-cookbook.git (push)
upstream  https://github.com/datawhalechina/jev-cookbook.git (fetch)
upstream  DISABLE (push)
```

如果换了一台机器、重新克隆后远程丢了，在仓库根目录执行：

```bash
git clone https://github.com/junfuhuang/jev-cookbook.git
cd jev-cookbook
git remote add upstream https://github.com/datawhalechina/jev-cookbook.git
git remote set-url --push upstream DISABLE
git fetch upstream
```

## 日常改代码

`main` 跟着原仓库走。自己的改动放在单独分支上，例如 `my-edits`。

```bash
git checkout -b my-edits
# 改文件、提交
git push -u origin my-edits
```

## 从原仓库拉更新

先把上游合进本地 `main` 并推回自己的 fork，再合进正在改的分支。冲突只出现在自己的分支里。

```bash
git fetch upstream
git checkout main
git merge upstream/main
git push origin main

git checkout my-edits
git merge main
```

## 贡献回原仓库

从自己的分支向 [datawhalechina/jev-cookbook](https://github.com/datawhalechina/jev-cookbook) 提 Pull Request。不要直接推 `upstream`。
