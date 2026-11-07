# BillyPro — GitHub 云端编译

本文件夹只包含云端编译所需的文件。把**全部内容**（包括 `.github` 隐藏文件夹）上传到 GitHub 仓库，Actions 会自动编译出 64 位的 `BillyPro.exe`。

## 步骤

1. 注册/登录 [GitHub](https://github.com)，右上角 **+** → **New repository**（Public 或 Private 均可；私有仓库免费账户每月 2000 分钟额度，本项目一次编译约 1～2 分钟）
2. 进入新建的空仓库，点 **uploading an existing file**，把本文件夹里的所有内容（含 `.github` 文件夹）一起拖进去 → **Commit changes**
3. 打开仓库的 **Actions** 标签页，会看到 "Build BillyPro" 正在运行（推送后自动触发，也可手动 **Run workflow**）
4. 运行出现绿勾后，进入该次运行详情页，底部 **Artifacts** 下载 `BillyPro-x64`
5. 解压得到 `BillyPro.exe`，与 **64 位** 的 `bass.dll` 放在同一目录即可运行

## 说明

- 编译配置：`Release | x64`（`bass.lib` 为 64 位导入库；vcxproj 的 Win32 配置未链接 bass.lib，勿用）
- `bass.dll` 运行时才需要，请从 [un4seen.com](https://www.un4seen.com/) 获取 x64 版，与 exe 同目录
- `dca_context.h` / `dca_frame.h` 取自 dcadec 源码（原 `dcadec_src.zip`），仅供 `BillyPro.cpp` 编译期引用
- 如果 Actions 报 msbuild 找不到工具集，可在 Build 步骤后追加参数 `/p:PlatformToolset=v143` 降级到 VS2022 工具集再试
