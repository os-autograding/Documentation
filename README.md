# 新的评测系统搭建方案
新的评测系统分为以下几个仓库
1. 源仓库（即需要评测的仓库）
2. 评测程序所在的仓库
3. 评测脚本所在的仓库
4. 排行榜仓库（可选）

## 评测流程
1. 源仓库提交后执行GitHub Actions.
2. Github Actions准备评测环境
3. Github Actions执行`make`进行内核编译(与比赛相同，要求能生成kernel-qemu文件和sbi-qemu文件)
4. Github Actions从目标仓库下载需要评测时所需要的镜像
5. Github Actions利用`qemu`执行内核 并利用 `tee`指令记录输出到指定的输出文件
6. 利用`os-autograding`进行评分

## 仓库设置
1. [源仓库设置](源仓库设置.md)
2. [评测脚本仓库设置](评测脚本仓库设置.md)
3. [评测程序仓库设置](评测程序仓库设置.md)

eg: 排行榜系统在原有的基础上进行了魔改。设置步骤相同，但是源代码略有改动，如需部署请拉取 [https://github.com/os-autograding/classroom-grading-template](https://github.com/os-autograding/classroom-grading-template)