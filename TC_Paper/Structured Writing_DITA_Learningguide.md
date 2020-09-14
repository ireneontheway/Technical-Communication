# DITA知识学习

## 介绍

DITA是一种基于XML的，与工具无关的创建，组织和管理内容的方法。

在DITA 中，topic由 map来组织，map更像是一个目录。

``` 
<title>This is a title</title>
```

DITA标签的名称取决于您创建话题的类型，例如< concept >, < task >, or < reference >。

结构化写作是一种自定义信息组合方式的工作流程。DITA中定义的元素有特殊关系和层级，也定义哪些元素前后联结以及特定元素的数量。其他结构化写作标准：DocBook, S1000D, NLM。

（样例）

- 基于topic的写作
- 将内容与格式分离
- 极简主义
- 结构化写作概念

## Topic

DITA的Topic是最基本的写作和重用单位，Topic由map组织，如同目录，map能够引导您了解Topic的层级和顺序。

|        | concept(glossentry)--What\Why                                | Task（Strict&General）--How | Reference                    |
| ------ | ------------------------------------------------------------ | --------------------------- | ---------------------------- |
| 作用   | 为什么要执行这个任务？执行任务前需要理解那些概念？（是什么意思） | 如何执行任务                | 执行任务时可能需要的参考信息 |
| 示例一 | 鸭的行为                                                     | 如何观察鸭                  | 鸭的品种                    |
| 示例二 | 油画的特点                                                   | 怎样画油画                  | 油画名家列表           |
| 示例三 | 洗衣机操作面板                        | 如何洗大件衣物？故障处理    | 错误代码参考                 |

> 1. 一个topic应该表述一个想法或回答一个问题
>
> 2. topic应该包含足够的信息来独立存在
>
> 3. topic不应假设任何上下文
>
> 4. 单个文件应仅包含单个topic

### 基础性结构

```
<topic id="sample">
   <title>Topic title goes here</title>
   <shortdesc>A short description</shortdesc>
   <body>
        (Most of the elements go here.)
   </body>
</topic>
```

- < shortdesc >（简短描述）元素通常用2-3句总结来描述topic内容。
- < title >是topic中唯一必需的元素。
- < body >包含topic的大部分信息。在特定topic类型中，body元素具有相关名称，例如对于概念的< conbody >和对于任务的< taskbody >。

### 常见元素

- < conbody > (Concept Topic的正文)
- < p > (一个段落)
- < ul > (一个无序列表或者项目符号列表)
- < ol > (一个有序列表或者编号列表)
- < li > (内嵌于< ul > 或< ol >里的一个列表项)
- < fig >(图片，包含一个可选标题)
- < image > (Figure里的图片或文本行间的图片)
- < section >  (Topic的一部分，带有可选标题)

### Task Topic

Task Topic回答“怎么做？”的问题，它包括完成过程的分步说明。DITA还允许包括步骤结果、图形、注释和一级子步骤。

- 严格任务：要求所有元素以特定顺序出现，适用于需要分步说明的项目。
- 一般任务：在元素排列的顺序上更为灵活，对过程概述很有用。

#### Strict Task 常见元素

- < taskbody > （Task的正文）

- < step >（步骤列序）

  - < cmd >（用户采取的动作，是step必需元素）

  - < info >（关于步骤的附加信息）

  - < stepresult >（执行操作后会发生什么）

  - < stepxmp >（举例说明如何做这个步骤）
- < example >（举例说明如何做整个Task）

### Reference Topic

Reference类型的Topic回答“是什么？”的问题。Reference类型的Topic通常包含描述性事实，例如命令或API函数调用的语法，以表格的形式列出设备的操作特性和容限范围，或识别软件屏幕上的信息项。

#### Reference Topic 常见元素

- < refbody >（Reference正文）
- < section >（Reference的一部分，带有可选标题）
- < table > （表格）
- < fig >(图片，包含一个可选标题)
- < properties >（属性列表）
- < refsyn >（语法图）

### Glossary Entry Topic

Glossary Entry类型的Topic回答“这个单词或短语是什么意思？”的问题。Glossary Topic通常包含一个术语，以及一个或多个定义。

#### Glossary Topic 常见元素

- < glossentry >（glossary entry topic类型）
- < glossterm >（单词或词组）
- < glossdef >（词汇表术语定义）

### 专门化

- 创建新元素，使其含有特定的顺序和特定的信息
- 创建新属性，使其来识别特定信息
- 创建与作者更加有关联的元素名称



## 元数据

*元数据* 提供有关信息的信息。例如，文字处理应用程序通常具有文档属性，它告诉你创建文件的人员和上次修改的日期。文档属性中的作者和修改日期不显示为文本信息。文档属性是关于文档本身的元数据。

带有ID属性的Topic示例

```
<Topic id="xyz">
	<Titlr>Title here</Title>
<body>
	...
	</body>元素
</Topic>
```

一般规则而言，读者不会看到元数据；他们会在搜索内容时过滤出元数据信息或用到元数据。

元数据可以分配在DITA内容中几个不同的位置：

- 在topic层面：DITA提供了一个< prolog >元素，其中存储整个topic的元数据
- 在元素层面：通常使用元素中的属性来指定元数据。
- 在map文件层面（map文件允许你集合多个topic以创建文档，帮助系统等；稍后的模块将更详细地解释map文件：以在引用topic的< topicref >元素中指定元数据。

```
<topic id="xyz">
  <title>Metadata example</title>
  <prolog>
    <author>Sarah O’Keefe, Scriptorium</author>
    <critdates>
      <created date="2015-05-01"/>
    </critdates>
  </prolog>
  <body>
    <p>Body content goes here</p>
  </body>
</topic>
```

## 创建DITA内容

DITA文件是XML，XML是纯文本。因此，可以在任何文本编辑器里创建一个XML文件。

- 一个基本的DITA Topic需要
- 一个XML声明
- 一个DOCTYPE 声明
- 一个topic
- 一个topic id属性
- 一个标题

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "topic.dtd">
<topic id="myfirsttopic">
  <title>Hello world</title>
</topic>
```

以上是一个最小有效的Topic.

```
?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "topic.dtd">
<topic id="myfirsttopic">
  <title>Hello world</title>
<body>
  <p>Here is a paragraph</p>
  <ul>
    <li>bulleted lists are nice</li>
    <li>especially if you have at least two items</li>
  </ul>
  <note>And don't forget the notes.</note>
</body>
</topic>
```

以上是含有主题内容的Topic。

### 用Oxygen Author创建一个Topic

### 注意、小心与警告

< note>元素用来创建注意、小心、警告和其他警告事项。

DITA为type属性定义了一些值：

- note（默认）
- attention
- danger
- caution
- important
- tip

``` 
<note type="warning">
不要给鸭子喂面包。面包不是一种健康的天然食品。
最好喂它们葡萄和玉米碎粒。
</note>
```

### 符号和编号列表

DITA中使用的最常用列表是无序（“符号”）列表（< ul >）和有序（“编号”）列表（< ol >）。

有序和无序列表都包含一个或多个列表项元素（< li >）。这些示例中所显示的<li>元素非常简单。但是，< li >元素可以包含文本数据和最常见的块元素以及内联元素。

DITA还定义了一个简单列表元素（< sl >），一种每个列表项中只包含几个词的列表。简单列表中的列表项使用< sli >元素。

### 块元素和内联元素

*块元素* 是一个段落级的元素，比如 p 标记（段落）， li （列表项）, 或者 codeblock （软件代码）。一般来说，块元素在页面上与其前后的信息中垂直分离。因此，如果在一行中有两个 p 标记，则在呈现信息时，它们以换行符分隔。注意，在XML中输入任何换行符都是无效的。

```
<p>This is a paragraph. </p><p>A second paragraph. </p>
```

*内联元素* 是一个在段落中提供标记的元素，比如< tm >（商标），< i >（斜体）, < xref >（交叉引用）, 或者 < term > （术语）。默认情况下，内联元素不会导致内容换行。

```
<p>An inline element <i>does not</i> result in line breaks. </p>
<p>The line breaks in the XML are
   <i>irrelevant</i>
to the output formatting.</p>
```

其他内联元素，例如以不同方式处理的< fn >（脚注）和< indexterm >（索引条目）。例如，处理< indexterm >条目以创建书籍后页的索引。< indexterm >的文本内容通常不会出现在内联元素出现的位置。

## 表格

DITA包含两种类型的表格：

- 简单表格

  < simpletable >元素支持基础表格的呈现形式，可定制性不强。

- 表格

  < table >元素支持复杂的表格类型，可以跨行跨列，能根据属性的设定精确地呈现。

另外还有两个非常独特的表格类型（基于< simpletable >元素）：

- < Properties >，用在Reference Topic中，用于定义属性列表。
- < Choicetable >，用在Task Topic中，用于显示各种选择之间的差异。

### 简单表元素

| 元素      | 描述         | number                                                       |
| --------- | ------------ | ------------------------------------------------------------ |
| < sthead >  | 标题行       | 最多只能有一个标题行。                                       |
| < strow >   | 正文行       | 必须至少有一个正文行，但该表可以包含许多行。                 |
| < stentry > | 一个简单表项 | 每行可以包含一个或多个<stentry>元素，但是每行（包括标题行）应当包括相同数量的<stentry>元素 |

### CALS 表（< table >）

| 元素      | 描述                                                       | number                                            |
| --------- | ---------------------------------------------------------- | ------------------------------------------------- |
| < title>   | 包含表的标题                                               | 零或一。                                          |
| < tgroup>  | 包含列参数，标题行和正文行                                 | 每个表必须至少包含一个< tgroup >元素。              |
| < colspec> | 定义列的宽度和标识信息                                     | 表格中每列应该有一个< colspec >元素。               |
| < thead>   | 包含表标题行                                               | < tgroup >最多可以包含一个< thead >元素。             |
| < tbody>   | 包含表正文行                                               | 一个< tgroup >有且只含有一个< tbody >元素。           |
| < row>     | 包含表中的一行                                             | < thead >或< tbody >元素可以包含任意数量的< row >元素。 |
| < entry>   | 包含表单元格的数据。可以包含文本数据或其他公共块和内联元素 | 一个< row >元素可以包含一个或多个< entry >元素。      |

### 最佳实践

- 在表格中，**总是将< entry >中的内容包裹在< p >标签内**，否则表格中的内容可能会变成意想不到的格式。
- 虽然DITA标准本身允许嵌套表格，但这并不是一个好主意。
- 在组织表格内容时，尽可能让表格包含更多行，而不是更多列。在输出内容时，**分页问题**可能会将多列展示成意想不到的样子。
- 在许多文字处理工具中，人们使用隐形表格来直观地呈现内容，比如缩进列表。在DITA里千万不能这么做，否则会导致意外的结果。
- 要**考虑表格里的内容被本地化后是否放得下**。如果可以的话，设计内容时，要考虑预留可增加到40％的文本扩展空间。
- DITA标准允许图形存在于单元格里。但是，在大多数情况下，最好将这些图形**限制为单元格中的小图标**。
- 创建表格时要**考虑到输出样式**。在小屏幕上呈现表格，不同设备所呈现出的表格差异很大（并且难以阅读），例如移动设备。
- 在某些情况下，您可能需要**考虑使用其他元素**，例如定义列表，可以作为表或词汇表样式列出，具体取决于目标输出。

## 创建Topic之间的关联

有多种不同的方式可以用来创建主题topic之间的关联：

- Map文件
- Conref
- 交叉引用
- 相关链接
- 关系表

### Map文件

Map文件用于根据输出的需要来组织内容结构。它们就像一个目录：在各种topic之间创建序列和层次结构。通常来讲，不要将所有可用的topic添加到map文件中——只用添加需要交付输出的topic。

Map文件主要由以下组件组成：

- topicref元素，提供特定主题的链接。
- mapref元素，提供另一个map的链接。

举例：

```
<map>
 <title>我的第一个map文件</title>
 <topicref href="ducks.dita">
   <topicref href="range.dita"/>
   <topicref href="size.dita"/>
   <topicref href="nests.dita"/>
  </topicref>
</map>
```

第一个topicref（ducks）包含了其他三个文件。Range.dita，size.dita和nests.dita 三个topic都从属于ducks.dita主题。

引用map的话，要用mapref来引用，而不是用topicref来引用。如果你想使用鸭子map内容作为另一个map的组件，你可以将它插入父map，如下所示：

```
<topicref href="fish.dita">
<topicref href="shorebirds.dita">
<mapref href="ducks.ditamap" format="ditamap"/>
```

### 转换map文件格式

大多数内容不使用DITA文件交付。取而代之，是将样式表应用于DITA文件以创建HTML，PDF或其他格式。这个过程称之为 转换。

DITA Open Toolkit是一个样式表集合，主要是用可扩展样式语言（XSL）编写的，为了更好的输出提供基础。用未修改的DITA Open Toolkit转换出来的默认结果显然是没有吸引力的。通常都会进行优化，以用于生产环境的内容转换和输出。

可以使用同一map文件进行转换获得两种不同的输出：一个是PDF文件，另一个是在线帮助系统。

### 交叉引用

交叉引用让你可以创建各种链接：从文本到文本中的其他位置，从文本到图形，从文本到表格，或从文本到网站

所有交叉引用使用< xref >元素。href属性指定交叉引用的目标。

还可以使用< xref >元素链接到DITA主题之外的资源。对于外部引用，需要设定一个值为external的scope属性和format属性，如下所示：

```
<xref href="http://www.learningdita.cn" scope="external" format="html"/>
```

在topic末尾，你可以插入相关链接元素（related-links）。使用关联链来接指向读者可能需要获取的额外信息。

相关链接包含一个链接和链接文本。请参见以下示例：

```
<topic id="sample">
    <title>Sample title</title>
    <body>
    ...
    </body>
    <related-links>
        <link href="http://www.example.com" format="html" scope="external">
            <linktext>Sample link</linktext>
        </link>
    </related-links>
</topic>
```

在link元素中，要指定目标（使用href属性）、格式和范围。对于网页链接和当前map文件之外的任何其他链接，必须指定范围scope =”external”。

注： 在map文件里，要避免直接用链接来关联不同的topic。它们受到与内联交叉引用相同的限制——链接可能会被断开。请改用关系表

### 关系表

关系表或reltable用来描述非顺序或非层次化的topic关系。Reltable是map文件的一部分，它可以出现在map中的任何位置，但一般是在主map的末尾添加reltable时用到。关系表的每一行包含链接到相关主题的topicref元素。

Reltable对关系的解析通常是 *不会* 显示在写作主题里的。

### 通过conref重复使用内容

在DITA中，可以通过conref重复使用内容。这些内容可能是警告信息（注意、小心和警告）或标准文本（例如公司地址）等。

如果你熟悉其它写作工具，可以把conref当作：

- Flare片段
- RoboHelp嵌入式主题
- FrameMaker文本插入和变量
- HTML服务器端引用

假设在名为location.dita的Topic中有以下注释：

```
<topic id="topicid">
    ...
    <note id="whatduckslike">鸭子更偏爱湖，而不是沙漠。</note>
    ...
</topic>
```

要在另一个主题中重复使用该注释，conref代码如下：

```
<note conref="location.dita#topicid/whatduckslike"/>
```

注： 目标元素必须与包含conref属性的元素具有相同的元素类型。比如你只能从一个 < note >元素conref到另一个 < note >元素；你也可以从一个< li >元素conref到另一个< li >元素，等等。
