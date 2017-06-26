# thucp

## 什么是thucp

thucp是一组基于Java开发的临床路径挖掘及分析工具集。

临床路径是针对特定病种的标准化诊疗计划，它已经成为一项重要的医疗管理工具，广泛用于提升预期疗效、控制医疗成本、减少资源浪费。在中国，自2009年起，国家卫计委先后发布并推广了超过1,000个病种的临床路径表单。当前，临床路径主要由专家研讨制定，然后交由各地具体实施，这类临床路径在实际应用中往往存在三个问题：1) 静态不变，更新费时费力；2) 实践性差，部署复杂，变异过多；3) 拓展性不足，难以应对繁多的病种（已知疾病10,000+）。

随着医疗信息化的快速发展，各地积累了大量的医疗数据，因此从数据中发现知识得到了越来越多的关注。我们的thucp工具箱围绕临床路径的不同应用领域，设计了一系列挖掘、分析工具，可以方便、快捷的从数据中发现有价值的信息，服务于临床路径的各类需求。thucp的输入文件主要包含两类数据，一是医疗日志数据，二是标准临床路径模板（特指国家卫计委发布的临床路径表单）。根据工具用途及输入输出要求，工具箱主要包含以下七方面功能：

### 功能1

>`输入`：医疗日志数据<br>
>`输出`：临床路径模型<br>
>`功能描述`：从医疗日志数据中，挖掘历史执行路径，客观反映数据中实际存在的常见医疗模式。模式包括医疗活动内容及活动间时序关系，前者由各种聚类算法（如主题模型、关联挖掘等）从繁杂的医疗日志数据中提取，然后交由过程挖掘算法抽取后者，从而生成最终的临床路径模型。<br>
>`潜在用途`：临床路径辅助设计/再设计；医保费用统计，病人、病种分类；年轻/基层医生教育。<br>

### 功能2

>`输入`：医疗日志数据<br>
>`输出`：异常诊疗过程<br>
>`功能描述`：判断每个患者的诊疗过程数据是否符合从整个数据中挖掘所得的临床路径模型。这里假定日志数据中大多数患者的诊疗过程是合理的，因此先从数据中挖掘得到临床路径模型，然后逐个对比患者数据与模型的差异，差异大的视为异常过程。<br>
>`潜在用途`：异常病例收集；医保欺诈检测。<br>

### 功能3

>`输入`：医疗日志数据 + 标准临床路径模板<br>
>`输出`：本地化临床路径模板<br>
>`功能描述`：根据本地的医疗日志数据，生成能够最大程度符合标准临床路径模板的本地化版本。标准临床路径在各地的部署实施过程中，变异率常常较高，一个可能的原因就是本地的临床路径设计没有充分考虑本地特点。因此可以从本地的历史日志数据出发，通过时序挖掘方法找出本地历史路径与标准路径的映射关系，生成符合本地特点的低变异率路径路径模板。<br>
>`潜在用途`：合理降低本地临床路径变异率；辅助本地临床路径系统设计及部署。<br>

### 功能4

>`输入`：医疗日志数据 + 标准临床路径模板<br>
>`输出`：合规性度量<br>
>`功能描述`：计算医疗日志数据与标准临床路径模板的符合程度。标准临床路径模板是医疗主管部门对于诊疗过程的重要管理工具，如何方便的考核各地的执行情况，依赖于合规性度量。<br>
>`潜在用途`：历史数据合规性检查；医保欺诈检测。<br>

### 功能5

>`输入`：已执行医疗日志数据 + 临床路径模型<br>
>`输出`：后续路径推荐<br>
>`功能描述`：将在院患者已执行的日志数据，与挖掘所得的临床路径模型进行匹配，找出当前所处阶段，根据频次、风险、费用等不同维度，给出后续路径的推荐。<br>
>`潜在用途`：临床决策支持；年轻/基层医生教育。<br>

### 功能6

>`输入`：医疗日志数据（可以多病种）<br>
>`输出`：多维度临床路径模型差异比较<br>
>`功能描述`： 对输入的医疗日志数据，从不同维度（病种、地区、医院、医生等）挖掘生成相应的临床路径模型，对不同模型的差异进行对比。<br>
>`潜在用途`： 相似病种诊疗过程对比；不同地区/医院/医生诊疗偏好对比。<br>

### 功能7

>`输入`：多个标准临床路径模板<br>
>`输出`：临床路径本体<br>
>`功能描述`：通过自动分析多个标准临床路径模板，提取共性特征，生成通用的本体结构。<br>
>`潜在用途`：建立临床路径本体库，统一临床路径形式。<br>

<br>
注：医疗日志数据，除特殊说明外，均指单一病种数据。

## 快速开始

thucp基于Java开发，需要配置环境包括JRE(8u40或以上，内嵌JavaFX)、ivy、JGraph，相关下载链接如下：

* JRE: <http://www.oracle.com/technetwork/java/javase/downloads/jre8-downloads-2133155.html>
* ivy: <http://ant.apache.org/ivy/download.cgi>
* JGraph: <https://www.jgraph.com/downloads/jgraph/>

1. 从Git将项目导入Eclipse <https://github.com/jintao05/thucp.git><br>
![git]<https://github.com/jintao05/thucp/raw/master/img/git import.png>

2. 修改JRE版本<br>

3. 确保ivy加载完所有依赖库<br>




## What is thucp
thucp is a set of java-based tools for Clinical Pathway (CP) mining and analysis. 

A Clinical Pathway refers to a standard diagnosis and treatment plan for specific disease. It is becoming one of the most important management tools for clinical quality imporvement, expense control and resource regulation. In China, more that 1000 CPs have been issued from 2009. However, most of current CPs are designed by experts mutually, so that they are always static and non-adaptive for clinical practice. 

With the rapid growth of clinical informatics, data-driven methods that discovering knowledge from clinical data are receiving more and more attention. Our toolbox thucp presents a series of data mining and analysis approachs for various CP applications include: 

  1. Execution Clinical Pathway Mining. An execution CP of a disease represents the most common clinical behaviors in the historical data. There are two core components for it: the kinds of behaviors and the relations between the behaviors. To achieve this goal, different clustering algorithms (k-means, topic modeling, association rule mining, etc) are firstly used for abstracting the complex clinical activities. Then, process mining methods are applied on these abstractions for deriving temporal relations. 
  
  2. Compliance Checking. Given an expert-designed or data-driven CP model, how can we evaluate the conformity degree between a patient record and the model. Various temporal analysis and process replay methods are presented for this task. 
  
  3. Clinical Desision Support. 
  
  4. Clinical Pathway Onotology. 

## How to install it
