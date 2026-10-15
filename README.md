# Transmute - LazyCat App

[Transmute](https://github.com/transmute-app/transmute)（自托管文件转换与压缩工具，3000+ 格式）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/transmute-app/transmute` 镜像经 `ghcr.1ms.run` 加速器拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag（`channel: stable`），发现新版本自动更新版本号与镜像、构建 LPK、发布商店。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。
- **单容器无依赖**：数据卷 `/lzcapp/var/transmute:/app/data`，健康检查 `/api/health/ready`。

## 结构

| 文件 | 说明 |
| --- | --- |
| `package.yml` | 包元数据（`community.lazycat.app.transmute`） |
| `lzc-manifest.yml` | 服务与路由配置 |
| `lzc-build.yml` | 构建配置 |
| `icon.png` | 图标 |
| `.github/lazycat-action.yml` | [lazycat-github-action](https://github.com/ca-x/lazycat-github-action) 配置 |
| `.github/workflows/lazycat.yml` | 构建 + 发布工作流 |

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

MIT（上游）
