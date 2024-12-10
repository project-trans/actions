### 使用说明

```yaml
- name: bot
        uses: project-trans/Display-Preview-URL-in-PR@SHA
        with:
          previewUrl: ${{ steps.deploy.outputs.deployment-url }}
          BOT_APP_ID: ${{ vars.BOT_APP_ID }}
          BOT_APP_SECRET: ${{ secrets.BOT_APP_SECRET }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          REMOVE_PREFIX: docs
          REMOVE_SUFFIX: .md
```