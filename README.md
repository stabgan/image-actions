# Image actions

Image actions will automatically compress jpeg and png images in GitHub Pull Requests.

- **Compression is fast, efficient and lossless**
- Uses mozjpeg + libvips, the best image compression available
- Runs in GitHub Actions, so it's visible to everyone

![Preview of image-actions pull request comment](https://user-images.githubusercontent.com/924/62024579-e1470d00-b218-11e9-8655-693ea42ba0f7.png)

## How to add this to your repository:

- Add the following steps to a workflow file found at: `.github/workflows/calibreapp-image-actions.yml` (If you don’t have one, create it.)
- Paste in the following:

```yml
name: Compress images
on: pull_request
jobs:
  build:
    name: calibreapp/image-actions
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@master
      - name: calibreapp/image-actions
        uses: docker://calibreapp/github-image-actions
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

The `GITHUB_TOKEN` secret is [automatically managed by GitHub](https://help.github.com/en/articles/virtual-environments-for-github-actions#github_token-secret). You do not have to manually create this secret. This automatic token is [scoped only to the repository that is currently running the action.](https://help.github.com/en/articles/virtual-environments-for-github-actions#token-permissions)

## Links and resources

- **[Announcement blog post](https://calibreapp.com/blog/compress-images-in-prs/)**
- [View calibre/image-actions on the GitHub Marketplace](https://github.com/marketplace/actions/image-actions)
- [Mozjpeg](https://github.com/mozilla/mozjpeg)
