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




