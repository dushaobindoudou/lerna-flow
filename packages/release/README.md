# `release`

> TODO: description

## Usage

```
const release = require('release');

// TODO: DEMONSTRATE API
```


## 发布版本

使用git commit 发布
会把最后一个commit放在package gitHead, 后面以这个作为包与registry对比来发布新版本，当上一次发布
失败的时候这个会很有用
```
git publish from-package 
```

通常建议使用, 会根据lerna version 来确定tag，并发布到git 然后把tag发布到npm，这个在CI中，手动变更版本会
是很好的场景
```
lerna version && lerna publish from-git 
```


默认的发布策略

根据上一次的发布找出修改的版本，通过使用leran version

```
lerna publish
```

使用tag发布版本

```
lerna publish --dist-tag alpha
```

alpha 版本升级到 canary 版本

```
lerna publish --dist-tag alpha
```

发布canary版本, 修改制定版本和preid
```
lerna publish --canary premajor --preid beta
```

转换成正式发布版本
```
lerna publish --conventional-commits --conventional-graduate --force-publish=@lernaflow/release --canary --preid alpha
```

canay版本转换成正式版本
```
lerna publish --conventional-commits --conventional-graduate --force-publish=@lernaflow/release
```

## 开发流程
1. 开发代码
2. 测试通过好发布alpha版本（业务版本需要进行测试验证)
3. 业务测试通过后发布canary版本（canary版本是未经过线上验证的版本，线上一段时间后没问题，则发布正式版本)
4. 线上验证如果有问题修改继续发布 canary，如果没问题则发布正式版本
5. 发布正式版本，如果正式版本有问题进行迭代


## 版本号
1. major 主版本不兼容（大功能改动、重大业务调整、影响比较大，需要重新测试）
2. minor 兼容功能需求修改（不相关的功能需要回归，改动需要测试）
3. patch bug修改（可以直接上线，只需要回归相关改动）


