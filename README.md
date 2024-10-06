## 使用说明

本说明适用于部署在 Cloudflare 的场景。对于其他部署方案，默认导出的 URL 变量名可能不是 `url`，需结合文档对 `steps.deploy.outputs.url` 后的变量名稍作修改。

1. 在 `deploy` 层级下使用 `outputs` 导出生成的 URL
2. 在 `jobs` 层级下引用工作流

## 代码样例

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    outputs:
      preview_url: ${{ steps.deploy.outputs.url }}
    steps:
      # 下方部署过程略
```

```yaml
      # 上方部署过程略
  comment_on_pr:
    needs: deploy
    uses: project-trans/actions/.github/workflows/comment-pr-preview-link.yml@main
    secrets: inherit
    with:
          previewUrl: ${{ needs.deploy.outputs.preview_url }}
```