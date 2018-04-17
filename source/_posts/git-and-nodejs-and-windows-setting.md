---
title: git和nodejs和windows常用配置
desc: git和nodejs和windows常用配置，提高开发效率
---

# 卸载windows 10 自带应用
```bash
Get-AppxPackage -AllUsers | Remove-AppxPackage
```

# windows添加cmd右键菜单
1. win + R 
2. regedit
3. HKEY_CLASSES_ROOT\Directory\Background\shell\cmd
4. 右键权限 - 高级 - 所有者 - 输入当前用户名 - 检查名称 - 确定 - 确定
5. Users - 完全控制 - 确定
6. HideBasedOnVelocityId 重命名为 ShowBasedOnVelocityId

# NODE JS
```bash
npm config set registry https://registry.npm.taobao.org
npm config set sass-binary-site http://npm.taobao.org/mirrors/node-sass
npm i yarn -g
yarn global vue-cli create-react-app http-server browser-sync gulp-cli webpack
```

# GIT
```bash
git config --global user.email "719012229@qq.com"
git config --global user.name "taoeer"
git config --global credential.helper store
git config --global alias.pl pull
git config --global alias.ps push
git config --global alias.unstage 'reset HEAD'
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global alias.co checkout
git config --global alias.st status
git config --global alias.cm commit -m
git config --global alias.br branch
git config --global alias.df diff
```