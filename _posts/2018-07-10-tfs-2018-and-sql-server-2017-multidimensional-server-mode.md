---
layout: post
title: TFS 2018 and SQL Server 2017–Multidimensional server mode
date: 2018-07-10 14:30
author: venhow
comments: true
categories: [IT资讯]
---
TFS2012成功升级到了TFS2018，因为安装SQL Server时候没有选择SSAS的模式（需要选择Multidimensional），默认是Tabular：

<blockquote><em>[Warning] An error was encountered while attempting to upgrade either the warehouse databases or the Analysis Services database. Reporting features will not be usable until the warehouse and Analysis Services database are successfully configured. Use the Team Foundation Server Administration console to update the Reporting configuration. Error details: TF400646: Team Foundation Server requires Analysis Services instance installed in the 'Multidimensional' server mode. The Analysis Services instance you supplied (&lt;INSTANCE NAME&gt;) is in 'Tabular' server mode. You can either install another instance of Analysis Services and supply that instance name, or you can uninstall this instance and install it in the required server mode.</em></blockquote>

Turns out that in SQL Server 2017 Analysis Services you can choose between 3 possible modes:

Relational modeling constructs (model, tables, columns), articulated in tabular metadata object definitions in <a href="https://docs.microsoft.com/en-us/sql/analysis-services/tabular-model-scripting-language-tmsl-reference">Tabular Model Scripting Language (TMSL)</a> and <a href="https://docs.microsoft.com/en-us/sql/analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo">Tabular Object Model (TOM)</a> code. This is the default value. OLAP modeling constructs (cubes, dimensions, measures). Originally an add-in, but now fully integrated into Excel. Visual modeling only, over an internal Tabular infrastructure. You can import a Power Pivot model into SSDT to create a new Tabular model that runs on an Analysis Services instance.

<table border="1" cellspacing="0" cellpadding="2">
<tbody>
<tr>
<td valign="top">
<blockquote><strong>Value</strong></blockquote>
</td>
<td valign="top">
<blockquote><strong>Description</strong></blockquote>
</td>
</tr>
<tr>
<td valign="top">TABULAR</td>
<td valign="top">Relational modeling constructs (model, tables, columns), articulated in tabular metadata object definitions in <a href="https://docs.microsoft.com/en-us/sql/analysis-services/tabular-model-scripting-language-tmsl-reference">Tabular Model Scripting Language (TMSL)</a> and <a href="https://docs.microsoft.com/en-us/sql/analysis-services/tabular-model-programming-compatibility-level-1200/introduction-to-the-tabular-object-model-tom-in-analysis-services-amo">Tabular Object Model (TOM)</a> code.</td>
</tr>
<tr>
<td valign="top">MULTIDIMENSIONAL</td>
<td valign="top">OLAP modeling constructs (cubes, dimensions, measures).</td>
</tr>
<tr>
<td valign="top">POWERPIVOT</td>
<td valign="top">Originally an add-in, but now fully integrated into Excel. Visual modeling only, over an internal Tabular infrastructure. You can import a Power Pivot model into SSDT to create a new Tabular model that runs on an Analysis Services instance.</td>
</tr>
</tbody>
</table>

More information: <a title="https://docs.microsoft.com/en-us/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas" href="https://docs.microsoft.com/en-us/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas">https://docs.microsoft.com/en-us/sql/analysis-services/comparing-tabular-and-multidimensional-solutions-ssas</a>

参考此文章更改Tabular模式为Multidimensional模式：<a href="https://cathydumas.com/2012/04/23/changing-an-analysis-services-instance-to-tabular-mode/">Changing an Analysis Services instance to tabular mode</a>。
