---
aliases: Cloud Migrations - The 6R
created_at: 2023-05-20 23:37
tags: aws
---

# 概念

将应用程序迁移到云的 6 个策略


# 用法

#### 1.     重新托管 — 也称为“简单地搬运”。

我们发现许多[早期云项目](https://medium.com/aws-enterprise-collection/getting-started-with-the-cloud-d5fd41dda652)倾向于使用云原生功能的全新开发，但在大型传统迁移方案中，组织希望快速扩大迁移规模以满足业务需求，我们发现大多数应用程序都被重新托管。例如，[GE Oil & Gas](https://aws.amazon.com/cn/solutions/case-studies/ge-oil-gas/) 发现，即使不实施任何云优化，该公司也能通过重新托管将成本降低大约 30%。

大多数重新托管可以通过工具自动进行 (例如，[AWS VM 导入/导出](https://aws.amazon.com/cn/ec2/vm-import/)、[Racemi](https://www.racemi.com/news_and_events/free-online-migrations-ibm-softlayer-made-easier-ever/))，但一些客户更喜欢手动完成此操作，因为他们可以学习如何将旧系统应用于新的云平台。

我们还发现，如果应用程序已在云中运行，它们将更易于优化/重新构建。对此，一部分原因是您的组织在这方面的技能更熟练了，另一部分原因是困难的部分 (迁移应用程序、数据和流量) 已经完成了。

#### 2. 平台重建 — 我有时称其为“修补再搬运”。

在这个阶段，您可能要进行一些云 (或其他) 优化以获得一些有形的收益，但您不能更改应用程序的核心架构。您可能希望通过以下方法缩短用于管理数据库实例的时间：迁移到数据库即服务平台，如 Amazon Relational Database Service ([Amazon RDS](https://aws.amazon.com/cn/rds/))，或将应用程序迁移到完全托管的平台，如 [Amazon Elastic Beanstalk](https://aws.amazon.com/cn/elasticbeanstalk/)。

我们合作的一家大型媒体公司将其在本地运行的数百个 Web 服务迁移到了 AWS，在这个过程中，它从 WebLogic (一个需要价格高昂的许可证的 Java 应用程序容器) 迁移到了 [Apache Tomcat](http://tomcat.apache.org/) (一个开源的等效容器)。除了从迁移到 AWS 所获得的成本节省和敏捷性，这家媒体公司还节约了数百万元的许可成本。

#### 3. 重新购买 — 迁移到另一个产品。

我最常将重新购买视为迁移到 SaaS 平台。将 CRM 迁移到 [Salesforce.com](https://www.salesforce.com/)，将 HR 系统迁移到 [Workday](https://www.workday.com/)，将 CMS 迁移到 [Drupal](https://www.drupal.org/)，诸如此类。

#### 4. 重新构建 — 重新设想如何构建和开发应用程序 (通常使用云原生功能)。

这通常由增加功能、扩大规模或提高性能的强大业务需求推动，而这些需求可能在应用程序的现有环境中难以实现。

您是否希望从单体架构迁移到面向服务 (或无服务) 的架构以改进灵活性或业务连续性 (我听说了一些在 e-bay 上订购大型机风扇皮带的故事)？这种模式往往是成本最高的，但如果您具有良好的产品-市场契合度，它也可能是最有益的。

#### 5. 停用 — 丢弃。

发现环境中的所有应用程序后，您可能会询问哪个职能领域拥有哪个应用程序。我们发现有多达 10% (我发现有 20%) 的企业 IT 产品组合不再有用，可以直接关闭。这些节省可以提高业务绩效，让您的团队将原本不足的精力放在人们使用的产品上，并缩小您必须保护的表面面积。

#### 6. 保留 — 这通常意味着“重新访问”或什么都不做 (就目前而言)。

您可能仍然能够承受一些折旧，没有准备好为最近升级的应用程序设定优先顺序，或者不打算迁移某些应用程序。您只应迁移对业务有意义的应用程序；并且，随着产品组合的倾向从本地变为云，您保留应用程序的理由可能会更少。  


# 对比



# 参考文献

