# NFT Minting dApp 入门指南

本指南将引导您如何使用 Ethereum 和 Next.js 建立一个全栈的 NFT Minting dApp。该项目使用 Solidity 编写智能合约，并用 React 和 TailwindCSS 构建前端界面。

## 前提条件

- 安装 [Node.js](https://nodejs.org/en/download/)
- 安装 [MetaMask 钱包浏览器扩展](https://metamask.io/download.html)

## 开始使用

### 克隆此仓库

使用以下命令将此仓库克隆到您的本地机器上：
```bash
git clone https://github.com/rutcader/rut-nft-minting.git
```

### 环境设置

复制 `.env.example` 文件为 `.env`，并填写 `HARDHAT_CHAIN_ID` 环境变量。示例文件中的端口在大多数情况下应该是可用的。

运行以下命令安装依赖：
```bash
npm install
```

### 本地运行智能合约

使用以下命令编译智能合约的 ABI：
```bash
npx hardhat compile
```
编译成功后，您将看到“Compilation finished successfully”的提示，并创建了一个 `src/artifacts` 文件夹。

接着，部署智能合约到本地区块链进行测试：
```bash
npx hardhat node
npx hardhat run scripts/deploy.js --network localhost
```
成功部署后，终端将显示智能合约部署的地址。

### 将本地账户添加到 MetaMask

打开 MetaMask 浏览器扩展，切换到 `Localhost 8545` 网络。

将步骤中生成的私钥添加到 MetaMask，例如 `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80`。

### 连接前端界面

在 `.env` 中设置 `NEXT_PUBLIC_MINTER_ADDRESS` 环境变量为您的智能合约地址，例如 `0x9fE46736679d2D9a65F0992F2272dE9f3c7fa6e0`。

在新的终端窗口中，使用以下命令加载前端界面：
```bash
npm run dev
```
如果需要使用不同的端口号（默认为3000），可以使用 `npm run dev -- --port=您的端口号`。

## 功能演示

设置完毕后，访问 `localhost:3000`（或您设置的其他端口号），在浏览器中查看您的 dApp。

首先，点击 `Connect wallet` 连接您的钱包，确保您已连接到 `Localhost 8454` 网络并选择了之前导入的钱包。

您现在可以测试 Mint 功能，每次交易可以 Mint 1 到 10 个 NFT。输入您想要的数量并点击 `Mint` 按钮进行 Mint。

如果 Mint 成功，您将看到 `Tokens minted` 数量的增加。

在 MetaMask 中切换账户将更新页面右上角的钱包地址。断开所有账户后，系统将提示您连接钱包。

浏览器刷新后，所有状态将保持不变。

## 编辑前端

要修改应用程序的首页，请编辑 `pages/index.js` 文件。

所有 [TailwindCSS 类](https://tailwindcss.com/docs) 都可供您使用。

使用 `npm run lint` 来检查您的前端代码。

## 测试

运行以下命令测试智能合约：
```bash
npx hardhat test
```
在 `test/Minter.test.js` 中找到基础测试用例。

## 发展路线图

- 显示已连接账户钱包中的资金
- 向合约添加常见的所有者功能