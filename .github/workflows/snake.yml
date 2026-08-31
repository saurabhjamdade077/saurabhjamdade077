name: Generate Snake Animation

on:
  schedule:
    # Runs daily at 00:00 UTC — pulls your real, live contribution graph each time
    - cron: "0 0 * * *"
  workflow_dispatch: {}   # lets you trigger it manually from the Actions tab
  push:
    branches:
      - main               # regenerate immediately whenever you push to main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    steps:
      - name: Generate contribution snake SVG/GIF
        uses: Platane/snk@v3
        id: snake-gif
        with:
          github_user_name: saurabhjamdade077
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
            dist/github-contribution-grid-snake.gif?color_snake=orange&color_dots=#bfd6f6,#8dbdff,#64a1f4,#4b91f1,#3c7dd9

      - name: Push output to "output" branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
