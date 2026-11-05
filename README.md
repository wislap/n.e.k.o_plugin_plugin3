# 3

Describe what this plugin does and how to configure it.

## Development

This directory is both the editable plugin source and its Git repository.

当前目录既是可编辑的插件源码，也是插件自己的 Git 仓库。

このディレクトリは、編集するプラグインソースであり、プラグイン自身の Git リポジトリでもあります。

When publishing to the plugin market, use this GitHub repository name:

发布到插件市场时，请使用以下 GitHub 仓库名：

プラグインマーケットへ公開する際は、次の GitHub リポジトリ名を使用してください：

```text
n.e.k.o_plugin_plugin3
```

From this plugin repository root:

```bash
uvx ruff==0.12.4 check --ignore-noqa --config ruff.toml .
```

From this plugin repository root / 在当前插件仓库根目录中 / このプラグインリポジトリのルートで：

```bash
uv run --project "../../../python/neko/N.E.K.O_clean4" neko-plugin sync . --clean
uv run --project "../../../python/neko/N.E.K.O_clean4" neko-plugin check .
uv run --project "../../../python/neko/N.E.K.O_clean4" neko-plugin check -r .
```

Python runtime dependencies are declared in `pyproject.toml` and synced into
`vendor/` for packaging. The generated `vendor/` directory is not committed;
local builds and CI recreate it before release checks.

Python 运行时依赖声明在 `pyproject.toml` 中，并在打包时同步到 `vendor/`。
生成的 `vendor/` 不提交；本地构建和 CI 会在发布检查前重新生成它。

Python ランタイム依存関係は `pyproject.toml` に宣言し、パッケージ化時に
`vendor/` へ同期します。生成された `vendor/` はコミットせず、ローカルビルドと
CI が公開前チェックで再生成します。

## Market release / Market 发布 / Market 公開

Publish the version declared in `plugin.toml`. By default this pushes the Git
tag, waits for the standard GitHub Release, and notifies the plugin market.

发布 `plugin.toml` 中声明的版本。默认会推送 Git tag、等待标准 GitHub
Release，然后通知插件市场。

`plugin.toml` で宣言されたバージョンを公開します。既定では Git tag を
push し、標準 GitHub Release を待ってからプラグインマーケットへ通知します。

```bash
uv run --project "../../../python/neko/N.E.K.O_clean4" neko-plugin publish .
```

To run only one half explicitly / 如需仅执行一部分 / 一方のみを実行する場合:

```bash
uv run --project "../../../python/neko/N.E.K.O_clean4" neko-plugin publish github .
uv run --project "../../../python/neko/N.E.K.O_clean4" neko-plugin publish market https://github.com/owner/repo/releases/tag/v0.1.0
```

The generated `.github/workflows/release.yml` builds and uploads
`plugin3.neko-plugin`. The market independently verifies that Release
before publishing it.

生成的 `.github/workflows/release.yml` 会构建并上传插件包；Market 会独立验证
该 Release 后再发布。

生成された `.github/workflows/release.yml` がプラグインパッケージをビルドして
アップロードし、Market はその Release を独立検証してから公開します。

## Entry

```toml
entry = "plugin.plugins.plugin3:Plugin3Plugin"
```
