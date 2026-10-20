# 01启动器 · 发版仓库（01-release）

本仓库只放 **01启动器** 的版本索引与安装包，不含源码。

## 目录

| 文件 | 作用 |
|---|---|
| `version-index.json` | 版本索引。启动器启动时读它判断有没有新版（地址写死在程序里） |
| 发行版附件 `01-launcher-x.y.z.zip` | 启动器本体，解压即用 |

## 索引格式

```json
{
  "schemaVersion": 1,
  "latest": {
    "version": "1.0.0",
    "url": "安装包直链",
    "sha256": "安装包 SHA-256（小写十六进制，64 位）",
    "notes": "更新说明",
    "publishedAt": "2026-10-20",
    "mandatory": false
  }
}
```

## 怎么用

1. 启动器「设置中心 → 高级选项」里的更新源留空即用本仓库内置地址；
2. 有新版本时，先上传安装包（发行版附件），再更新 `version-index.json` 的 `version` / `url` / `sha256`；
3. 用户端「检查更新」→ 下载 → 校验 → 重启替换。

## 下载 1.0.0（分卷）

> 安装包 139.5MB，超过 Gitee 单文件 100MB 限制，已拆成 **2 个分卷**放在发行版附件里。

1. 下载两个分卷：
   - `01-launcher-1.0.0.zip.part00`（90MB）
   - `01-launcher-1.0.0.zip.part01`（50MB）
2. 合并（Windows 命令提示符，两个文件放同一目录）：
   ```bat
   copy /b 01-launcher-1.0.0.zip.part00 + 01-launcher-1.0.0.zip.part01 01-launcher-1.0.0.zip
   ```
   > 也可以用 7-Zip：右键 `part00` → 7-Zip → 提取到当前文件夹。
3. 解压得到的 `01-launcher-1.0.0.zip`，双击 `01.exe`。
4. 合并后 SHA-256：`8e0b9a45e4de2053a2527e2cc6f7bcce06027c39bb453321e3807a6e5279af38`

## 许可

见 `LICENSE`。
