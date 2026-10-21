# 01启动器 · 发版仓库（01-release）

本仓库只放 **01启动器** 的版本索引与安装包，**不含源码**（闭源发布）。

- 安装包（139.5 MB）放在 **Releases** 里（GitHub 仓库单文件上限 100 MB，但 Release 附件单个可到 2 GB，所以安装包不进仓库本体）。
- 仓库本体只放 `version-index.json` 和文档，克隆很快。

## 目录

| 文件 | 作用 |
|---|---|
| `version-index.json` | 版本索引。启动器启动时读它判断有没有新版（地址写死在程序里） |
| Releases 附件 `01-launcher-x.y.z.zip` | 启动器本体，解压即用（**单个整包，不再分卷**） |

## 下载安装（1.0.0）

1. 打开本仓库右侧的 **Releases** → `v1.0.0` → 下载 `01-launcher-1.0.0.zip`（139.5 MB，单个文件，不用合并）。
2. 解压到**纯英文路径**（例如 `D:\01-comfyui`；不要放 `C:\Program Files`，也不要中文路径）。
3. 双击 `01.exe`，按首启向导选运行时与 ComfyUI 目录即可。

**SHA-256（下载后建议核对）**

```
d65996ec74631e8b07c413c9ca88654da2c4b1801fbbef810ed48ffce8977c42
```

Windows 校验方法（命令提示符 / PowerShell）：

```powershell
Get-FileHash .\01-launcher-1.0.0.zip -Algorithm SHA256
```

> 校验值不一致 = 下载过程中损坏，删掉重下。

## 索引格式

```json
{
  "schemaVersion": 1,
  "latest": {
    "version": "1.0.0",
    "url": "安装包直链（Release 附件地址）",
    "sha256": "安装包 SHA-256（小写十六进制，64 位）",
    "notes": "更新说明",
    "publishedAt": "2026-10-22",
    "mandatory": false
  }
}
```

## 怎么发版（维护者）

1. 打包 → 得到 `01-launcher-x.y.z.zip`；
2. 在 GitHub 建 Release（tag 例如 `v1.0.0`），把 zip 上传为**附件**；
3. 更新 `version-index.json` 的 `version` / `url` / `sha256` / `notes` / `publishedAt`，提交；
4. 用户端启动 → 自动检查 → 下载 → SHA-256 校验 → 重启替换（模型、节点、设置原位保留）。

`url` 填 Release 附件的直链，格式：

```
https://github.com/<用户名>/01-release/releases/download/<tag>/01-launcher-x.y.z.zip
```

## 版本历史

| 版本 | 日期 | 说明 |
|---|---|---|
| 1.0.0 | 2026-10-22 | 首个版本。包含：下载管理（断点续传 / 移除三选一）、工作流检查与一键补齐、节点/模型/内核/组件管理、启动参数自动调优、错误翻译官降噪、文件夹映射（可取消）、启动器自更新 |

## 许可

见 `LICENSE`。
