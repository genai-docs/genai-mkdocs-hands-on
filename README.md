# genai-mkdocs-hands-on

## ハンズオン手順

1. [VS Code (code-server) の初期化](manuals/01.vscode.md)
2. [GitHub リポジトリの準備](manuals/02.github.md)
3. [MkDocs の利用](manuals/03.mkdocs.md)
4. [textlint を活用する](manuals/04.textlint.md)
5. [Pull Request を送る](manuals/05.pull_request.md)
6. [PDF 化する](manuals/06.pdf.md)
7. [Mermaid 記法](manuals/07.mermaid.md)
8. [Marp によるスライドの作成](manuals/08.marp.md)
9. [.pagesファイルによるナビゲーション指定](manuals/09.pages.md)


## AIエージェントのサインイン手順

- [Claude Code](03.claude-code.md)
- [Cursor CLI](04.cursor.md)
- [Codex CLI](05.codex.md)
- [GitHub Copilot CLI](06.copilot.md)

## WSL で VS Code から利用する

前提：

- Dockerが利用できる環境
- VS Code
- VS Code拡張 `Dev Containers`

手順（WSL）:

1. WSLなどでこのリポジトリーをフォークし、クローンする

   ```bash
   cd ~
   git clone https://github.com/your-username/genai-mkdocs-hands-on.git
   ```

2. WSLでこのリポジトリーを開く。

   ```bash
   cd genai-mkdocs-hands-on
   code .
   ```

3. VS Codeで `Reopen in Container` を実行する。
4. 初回起動時は `.devcontainer/devcontainer.json` にしたがって依存関係が自動で導入される。

