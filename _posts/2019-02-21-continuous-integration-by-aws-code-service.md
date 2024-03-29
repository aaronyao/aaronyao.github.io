---
layout: post
title:  "使用AWS Code服务构建持续集成环境"
categories: 持续集成 AWS CodeBuild CodeDeploy CodePipeline
typora-root-url: /Users/aaron/Google Drive/blog/aaronyao.github.io
---
在做了多年的软件开发和技术管理工作后，发现很多团队仍然停留在手工作坊的阶段，还没有踏上IT自动化这条路，这是一定需要去改善的。

##### 持续集成简介
**持续集成**是一种软件开发实践，即团队开发成员经常集成他们的工作，通常每个成员每天至少集成一次，也就意味着每天可能会发生多次集成。每次集成都通过自动化的构建（包括编译，发布，自动化测试）来验证，从而尽早地发现集成错误。

这是[Martin Fowler](https://martinfowler.com/articles/continuousIntegration.html)对持续集成的解释，实际的工作中的持续集成，简单理解为下面四个过程：
1. 开发者在完成自测（包括单元测试）后，向源代码服务器提交代码；
2. 源代码服务器触发自动构建过程；
3. 执行自动化测试过程（包括所有单元测试和集成测试）；
4. 让软件达到`待验证`状态。

##### 作用和要点

持续集成通过整合利用各种工具（源代码服务器，持续集成服务器，以及相关的脚本语言），构建了一个IT自动化的开发和测试环境，进而在这个环境中进行持续集成的实践。

- 最显著的作用是*尽早的*发现BUG从而修复BUG;
- 同时，由于*IT自动化*的引入，避免手工编译部署过程产生人为错误，提高开发团队的效率。

在实践持续集成的过程中，有一些要点：

- 代码必须本地编译成功后，才能提交待源代码服务器；
- 应该至少每天把代码提交到主线，与其他开发者进行协同；
- 立即修复失败的自动化构建；
- 构件完成的软件包，应该能容易的被整个团队获取和访问；
- 向整个团队展示持续集成的过程和结果（构建一个Dashboard）。

##### 持续交付和持续部署
持续集成发生在新项目或项目某个版本的研发周期内（一次交付内），要求开发者尽早提交代码，与开发团队进行代码层面的协同，提前发现代码集成的问题。

持续集成完成后，软件达到了一种`待验证`的状态。在整个软件的研发周期中，还会有一些后续工作，包括在不同环境进行QA测试，配置部署等阶段。所以，伴随持续集成，后续还有两个实践，持续交付和持续部署，

- **持续交付**是指代码完成持续集成后，自动化地把代码部署到不同环境（testing/staging）进行测试和验证，最终让代码达到一种`可交付`的状态； 
- **持续部署**是在持续交付的基础上，把生产环境部署的过程自动化。

下图解释了CI/CD在软件开发各周期上跨度的不同，

![CI/CD](/assets/images/cicd-phase.png)

#####  AWS Code服务 

通常，持续集成中用的的比较流行的工具，都有以下这些，

| Source control | Build | Test | Deploy | Orchestrate |
|--------------|-----|----|------|------|
| Github | mvn | xxx | bash | Jenkins Pipeline |
| Github | mvn | xxx | bash | Jenkins Pipeline |


AWS除了云自身产品外，还自研了一系列的[开发者工具](https://amazonaws-china.com/products/developer-tools/)，从IDE，源代码服务器，代码构建工具，部署工具，以及CI/CD用到的Pipeline，基本上是从头到尾都干了一遍，可见AWS的未雨绸缪和野心。

| Source control | Build | Test | Deploy | Orchestrate |
|--------------|-----|----|------|------|
| CodeCommit | CodeBuild | 3rd party | CodeDeploy | CodePipeline |



#####  案例
- Github托管源代码
- Webhook通知代码编译


