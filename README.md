# kustomize-issue-7f53131c-0253-45a9-87c4-c6ab2f4d55ea

This repository is an example to reproduce an issue I'm having with [kustomize](https://github.com/kubernetes-sigs/kustomize).

If you run `kustomize build .` in the root directory, you get an error like:

```
Error: accumulating resources: recursed merging from path '2cbace6b-c9f0-4f56-aba7-b911c0c85d48': var 'MYSQL_SERVICE' already encountered
```

The root directory kustomization simply composes the two directories in here (which are identical and both use [etherpad-lite](https://github.com/gobengo/etherpad-lite) as a base).

`kustomize build` in either of the base directories works fine and produces a stream of yaml output (try `ls -d */ | xargs -L1 kustomize build`). 

Expected Behavior: I can `kustomize build .` in the root directory and there is no error and I see the same output as concatenating the outputs of the two bases (joined with '---').

