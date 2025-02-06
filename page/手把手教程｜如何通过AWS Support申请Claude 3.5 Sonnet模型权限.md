# 手把手教程｜如何通过AWS Support申请Claude 3.5 Sonnet模型权限

## ▍AWS区域选择建议
开通前需确认选择美国东部（弗吉尼亚北部）us-east-1或美国东部（俄亥俄州）us-east-2区域，这两个区域可提供最完整的AWS资源和服务支持。

![AWS区域选择示意](https://bbtdd.com/wp-content/uploads/img/789207570909.webp)

---

## ▍申请操作全流程
### 1. 登录AWS管理控制台
通过可信凭证登录亚马逊云科技控制台，确保账号具有IAM管理权限。

### 2. 进入支持中心
控制台右上角导航栏找到`支持`下拉菜单，选择`支持中心`进入工单系统。

![支持中心入口指引](https://bbtdd.com/wp-content/uploads/img/411326386541.webp)

### 3. 新建支持工单
按业务需求创建技术咨询工单，工单类型选择`Service Limit Increase`，在description中详细说明需要开通Claude 3.5 Sonnet的使用场景。

![工单创建界面](https://bbtdd.com/wp-content/uploads/img/10457038191.webp)

### 4. 等待审核批复
通常2-4个工作日内会收到邮件通知，审批后在Bedrock服务中即可看到模型访问权限变更。

![权限开通状态示意](https://bbtdd.com/wp-content/uploads/img/57462854548.webp)

---

## ▍模型访问配置指南
### 权限激活步骤
1. 访问Amazon Bedrock控制台
2. 进入`模型访问权限`模块
3. 点击`Modify model access`开始配置

![Bedrock控制台入口](https://bbtdd.com/wp-content/uploads/img/587488138449084.webp)

### 模型选择技巧
在可申请模型列表中找到`Claude 3.5 Sonnet`系列，建议同步勾选基础模型和微调版的访问权限。

![模型勾选界面](https://bbtdd.com/wp-content/uploads/img/0280659056721529.webp)

### 提交与验证
确认选择后点击`submit`等待系统审核，当状态显示`Access granted`即可进行API调用。

![权限激活流程演示](https://bbtdd.com/wp-content/uploads/img/6421760631.webp)

👉 [野卡 | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/yeka)

---

## ▍开发者资源推荐
通过Bedrock的`游乐场`功能可快速验证模型效果，官方文档提供了完整的SDK集成指南。建议创建Dedicated Capacity确保服务质量，注意合理配置Rate Limits避免超额使用。

![模型运行测试界面](https://bbtdd.com/wp-content/uploads/img/86071288.webp)

---

## ▍AI云服务加速方案
对于需要快速构建跨国AI应用的用户，推荐使用全球分布式部署方案。通过虚拟信用卡解决海外服务订阅痛点：

👉 [野卡 | 三分钟快速生成海外支付工具](https://bbtdd.com/yeka)（邀请码：ACCPAY）