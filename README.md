# luk-data-backup

feiye885/luk-data 的灾备仓库。每周五深度巡检生成完整 git bundle（含全部分支和历史），以固定文件名覆盖提交；旧版本保留在本仓库的 git 历史里。只增不删。

| 文件 | 内容 |
|---|---|
| luk-data_latest.bundle | luk-data 全部提交和分支（`git bundle create --all`） |
| lfs-objects_latest.tar | luk-data 的 LFS 文件（有 LFS 文件后才生成） |
| 灾备记录.md | 每次灾备的日期、提交号、SHA-256 |

## 恢复方法
```
git clone luk-data_latest.bundle luk-data
cd luk-data
mkdir -p .git/lfs && tar -xf ../lfs-objects_latest.tar -C .git/lfs   # 有 LFS 包时
git lfs checkout
```
