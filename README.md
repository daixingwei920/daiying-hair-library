# 戴影公共发型测试库

戴影 AI 发型设计插件 0.4.0 的独立公共素材源：24 款正面发型，女款 14、男款 10，按年龄、性别、长度、卷度与发色分类。素材来自项目 AI 生成的虚构成年模特与透明头发层，没有收录网络人物照片、顾客原照或门店私人作品。

这是公开测试库。使用和分发范围见 [LICENSE](LICENSE)，不标 CC0，不代表真人、儿童、全部款式视觉或商业发布已验收。款式通用特征可来自选款研究，网络人物图片未作为这些文件分发。

## 插件接入

后台“公共 Git 发型库”填写：

- 清单：`https://raw.githubusercontent.com/daixingwei920/daiying-hair-library/main/library.json`
- SHA-256：复制 [library.sha256](library.sha256) 中的值，核对文件字节后手动同步。
- 确认素材公开分发与试戴的使用范围符合 [LICENSE](LICENSE)。

为可复现接入，可把上述 `main` 换为清单所在完整 commit。清单中的图片均固定到素材 commit；清单或素材更新需要重新核对哈希，不自动跟踪 main。服务器只保存清单，图片由浏览器按需 GET、校验后显示。导入项强制 `git-` 前缀，不覆盖私人库，不自动获得 AI 校准资格。

已有插件内置同样 24 款，接入本库后会作为独立 Git 分类显示；不会自动移除内置副本。本库不是另外新增 24 种发型。

## 文件与更新

`catalog.json` 是使用相对文件路径的源清单，`library.json` 是插件可消费的、固定素材 commit 的清单；`provenance.json` 记录每个文件及输入哈希。`assets/` 仅包含 24 张透明正面与 24 张缩略图，均为静态 WebP。早期六款按既有试戴画布导出 512×640 版本，其余文件按原字节保留。

更新顺序：先提交素材/catalog/provenance 得到 commit A；再用 A 构建每个图片的 raw URL、生成 library.json 及 SHA-256，提交清单 B。不要让清单用自身 commit 作循环引用。保持许可和来源记录；素材不能带顾客原图、私库内容、密钥或生产配置。

不包含侧背视图、模型文件、Core 源码、AI API 调用或自动发布工作流。

## Stable 商业试戴授权

`library-stable.json` 是 stable 专用固定清单，素材仍使用原固定字节；见 [Stable 许可](LICENSE-STABLE.txt)、[SHA-256 清单](asset-rights-stable.json) 和 [清单哈希](library-stable.sha256)。原测试库和 `library.json` 保持原许可。
