# Completeness 完整性

> A successful book is not made of what is in it, but what is left out of it. ——Mark Twain

对用户而言，保证技术文档的完整性指的是能够获取所有所需信息。首先需要了解用户，了解信息的写作是出于什么目的。比如说，用户需要完成特定的任务吗？需要学习相关概念吗？需要通过信息做决策吗？文档人容易写得太多，把所有东西都塞在一个主题里，其实我们需要一个统一信息的导航。

文档人需要采用极简主义来写作，大刀阔斧地精简技术信息，只留精华部分。这样，用户在了解基本概念之后可以自己轻松探索产品。文档的完整性和其他质量特点类似，特别是task orientation, organization, retrievability，文档的完整性也和视觉特效的特点类似。文档人通常是需要用图来解释技术概念的。此外，建议采用实用性测试来帮助自己了解那里缺少信息，哪里信息冗余。以下是一些规范指南：

- 只涵盖支持用户任务的所有 topic
- 每个 topic 都要概括尽多的用户所需信息
- 使用信息模块保障合适的覆盖率
- 只有用户非常需要时才重复信息

接下来我们一一来分析。

## 只涵盖支持用户任务的所有 topic

技术信息的目标用户需要知道如何使用产品完成自己的工作任务。建议结合 task orientation 的质量信息特点，了解用户和其任务之后才能选择相关 topic。

最小的 task topic 是对主要任务、子任务的描述、操作场景和原因、如何应对可能出现的错误。在你的写作项目早期就应该进行任务分析，了解用户会做的子任务、任务都有哪些。在之后，你可以使用任务分析结果评估写作的信息是否包括以下必须的 topic:

- 是否包含所有大型用户任务？
- 是否描述了用户完成大型任务中涵盖的子任务
- 是否解释了相关可选任务的原因和场景应用
- 是否描述可能出现的错误

如果以上问题回答“是”，那么你应该涵盖了所有能满足用户需求的 topic。

无论作者对产品如何熟悉，写文档时都容易想当然。因此一定要做完整的任务分析，而不是主观臆断。

同时，在解释概念的时候，比方说引入一个事务、解释一段流程或者强调一个优势，不要混淆信息概念和产品内部资料。概念是在宏观背景下向用户展示某一方面，或者是解释必要的术语，用户通过学习必要的概念来了解所需的信息。打个比方，文件夹就是文字处理程序中的一个概念，但该程序是在内部如何呈现和操作文件夹的就不该告诉用户了。要时刻谨记，与用户任务无关的信息都不应该写进文档。

## 每个 topic 都要概括尽多的用户所需信息

这个指南要关注两点“尽多”和“所需”，这就是讲究如何详略得当的问题了。核心任务就是了解用户。你要了解新老用户在使用产品时的体验，这会帮助你决定哪些信息是相关的，哪些是不相关的。当用户差不多都是一类人群时，写文档试试最方便的。一方面，假如说是为全新的产品写文档，可以假定用户都是出于好奇心来关注这个产品。另一方面，如果是为早就在市面上的产品写文档，就可以假定用户都是老手了。

但我们常常遇到的问题是，用户不尽相同。既不想让老用户看到老生常谈的介绍信息，又不想让新用户难以上手。

![DQTI_Accuracy_Completeness_users](Picture/DQTI_Accuracy_Completeness_users.png)

因此需要区别对待，如果用户对文档熟悉程度不同，就需要想办法满足不同的信息需求了。以下是一些建议：

- 建立独立的 concepts、task、reference 的 topic。将任务 topic 和 concept、reference 的 topic 链接起来。
- 为老用户提供线上线下的信息，为新用户额外提供入门的在线指南。
- 提供两个版本的信息格式，比如说为老用户提供 advanced topic，为新用户提供教程。
- 将信息整合在一个在线信息系统里或者印刷文件中，但在 advanced topic 中剔除引入性 topic。
- 将信息整合在一起，但是使用图形进行区分。

熟悉用户之后，还是要牢记我们写入的内容要遵顼以下两点：

- 尽多：提供足够多的信息

  - 可能的信息

    普遍和少见的情况都要提及。特别是要提供少见场景下的特殊信息。比如说，某种操作失败的情况应如何处理等等。

  - 流程

    写指南的时候要跟随流程的所有路径以用户视角走一遍。流程中的决策点越多指南的作用越大。

  - 链接和交叉引用

    提示用户其他参考信息的时候，要问问自己用户需亚奥知道什么。不要仅仅给出标题。比如说不要写 “For more information, see *InfoDBase User’s Guide*,”  应该换成 “For information about indexing in InfoDBase, see *InfoDBase User’s Guide*.” 。不要让用户只有点击链接才能了解里面的内容。同时要注意如果使用超文本链接需要选择完整的链接文本。

    描述交叉引用也能帮助在以后更新版本时验证其正确性。

  - 程序语法

    记录命令、调用、语句或宏的语法时，询问程序员到底需要展示多少细节。

- 所需

  - 过多冗余的细节会降低效率，用户会更难寻得需要的信息。John Carroll 在他的书 *The Nurnberg Funnel: Designing* Minimalist Instruction for Practical Computer Skill* 提到：

  > 极简的方法是指读者花最少的精力就能获取需要的信息。

  - 许多引入性 topic 的信息超出了用户所需。问问自己信息有第二阶梯读者吗。如果有，他们和主要读者的差别在哪里，对于他们现有信息是多了还是少了。