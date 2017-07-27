# 覆盖率工具
## 使用：

- npm cover: 执行代码单元测试、生成测试覆盖率
 
## 构建过程：

- package.json包，需要istanbul，mocha，在本地生成覆盖率情况
- 在travis ci里面加上变量`COVERALLS_SERVICE_NAME`(当前开发的系统名)和`COVERALLS_REPO_TOKEN`（coveralls的token码）
- 在package.json文件里配置任务脚本，
`istanbul cover ./node_modules/mocha/bin/_mocha --report lcovonly -- -R spec && cat ./coverage/lcov.info  && cat ./coverage/lcov.info | coveralls && rm -rf ./coverage`
(先进行测试，生成lcov报告，把报告结果发送coveralls里，删除coverage目录)

## 注意

coveralls.yml文件不会上传到服务器，本地测试需要用到。

## 参考资料

- 覆盖率工具：[https://github.com/gotwarlost/istanbul](https://github.com/gotwarlost/istanbul)
- 单元测试框架：[https://github.com/mochajs/mocha](https://github.com/mochajs/mocha)
- 覆盖率信息上传工具：[https://github.com/nickmerwin/node-coveralls](https://github.com/nickmerwin/node-coveralls)

# 版本号升级

## 使用：
`grunt release <? patch(bug修改),minor(新功能),major(项目架构升级)>`，对应的版本号：`<major>.<minor>.<patch>`

## 变化

- 项目增加新Tag
- package.json内的version升级
- 产生更新日志
- 产生一个新的提交信息，并包含在当前的tag内
 
## 关联操作

生成日志，版本升级时会把现在所有的commit信息做成list放在CHANGELOG.md里，形成更新日志

## 参考资料

- 升级规则：[https://www.npmjs.com/package/grunt-bump](https://www.npmjs.com/package/grunt-bump)
- commit提交规范和更新日志配置：[https://github.com/commitizen/cz-cli](https://github.com/commitizen/cz-cli)

# 代码打包压缩

## 使用

- grunt dist

## 变化

- 把所有源代码打包成一份代码，fn.js，放在dist目录下
- 再把fn.js压缩成fn.min.js

# 代码格式检查

## 使用

- grunt format

## 变化

- 检查所有js代码格式，不合格的格式会在控制台给出提示



