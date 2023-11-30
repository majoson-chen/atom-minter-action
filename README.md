# atom-minter-action

使用 github actions 跑 atomicals-cli

## how to use

1. fork 本仓库, 然后进入自己的仓库
2. 点击 github action，点击绿色按钮 enable，随后在左边选择 `RUN-ATOM-CLI`，可以看到右边出现一个 `run workflow` 的按钮。
3. 填写参数：  
    - 执行的命令：你要执行的命令，例如 `mint-dft pepe`，不需要添加 `yarn cli` 前缀
    - 钱包文件: 在本地的 `atomcials-cli` 创建好钱包后，复制整个 `wallet.json` 并粘贴
    - 节点地址：如果你有私有节点，可以选择这个，如果你的节点搭建在本地，则无法使用
    - 执行次数：希望执行命令多少次，请注意，并非一定每次执行都会成功，所以，如果你希望把你钱包里的钱都打完，请给一个足够高的数，例如 10w。每个启动的 `actions` 最多可以执行六个小时。

## 安全问题

由于将 `wallet.json` 文件粘贴到 `actions`，因此不确定是否存在安全隐患，至少目前看来是看不到相关内容。如果你很在意，可以在打完之后及时将钱转走。

如果你使用的是其他人 `fork` 过的仓库，请注意代码是否被修改。

## 多开问题

可以在本地的 `atomicals-cli` 执行 `yarn cli wallet-init` 生成钱包后，将同目录下的 `wallet.json` 文件剪贴到别的文件夹中。然后再执行一次 `yarn cli wallet-init`，如此往复，你就得到了多个钱包地址。

随后你可以向钱包的 `funding` 地址转钱，然后在 `actions` 中填入不同的钱包信息，就可以实现多开(貌似免费最多同时并行20个)。
