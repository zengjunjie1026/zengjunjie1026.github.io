---
title: hexo-back-up-bug
date: 2023-10-16 15:11:20
tags:
---


修改hexo-git-backup的git.js

```js

 for (var t in repo){
        commands.push(['push', '-u', t,   repo[t].branch, '--force']);
		//commands.push(['push', '-u', t, 'master:' + repo[t].branch, '--force']);
}
```