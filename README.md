# TableSense for spreadsheet table detection

Spreadsheet table detection is the task of detecting all tables on a given sheet and locating their respective ranges. Automatic table detection is a key enabling technique and an initial step in spreadsheet data intelligence. To enable data-driven models, we annotated a large amount of table ranges on real spreadsheet data. Our annotations are based on three public datasets (VEnron2, VEUSUS, and VFUSE), which are widely used in spreadsheet domain. To eliminate similar spreadsheets that may introduce lots of duplicated labeling efforts, we use [the published dataset](https://figshare.com/projects/Versioned_Spreadsheet_Corpora/20116) which has clustered similar sheets by [SpreadCluster](http://www.tcse.cn/~wsdou/project/venron/):
1.	VEnron2 is built on the Enron email archive by SpreadCluster (MSR 2017). It contains 1,609 evolution groups and 12,254 spreadsheets.
2.	VEUSES is built on EUSES by SpreadCluster (MSR 2017). It contains 177 evolution groups and 363 spreadsheets.
3.	VFUSE is built on FUSE by SpreadCluster (MSR 2017). It contains 188 evolution groups and 1,143 spreadsheets.

Note that the WebSheet dataset introduced by [TableSense](https://www.microsoft.com/en-us/research/uploads/prod/2019/01/TableSense_AAAI19.pdf) needs to solve compliance issues before publishing, so we firstly publish annotations for VEnron2, VEUSUS, and VFUSE to facilitate recent research.
To process raw Excel files, we first transformed original Excel files from .xls to .xlsx. Second, we tried to read and extract features from these files using ClosedXML. We excluded those files that failed to transform and process. Then we seleceted one file for each cluster, and labeled only the first two sheets for those files containing multiple spreadsheets. All sheets had been labeled and checked by no less than two persons. We excluded those controversial cases between annotators. Finally we got 2,615 tables from 1,645 spreadsheet. Since VEnron2 has the greatest number of clusters, it contributes most annotated table ranges. The annotation schema looks like the following example:

File name     | Sheet name | Training/testing | File folder  | Table region 1 | Table region ...
--------------|:----------:|:----------------:|:------------:|:--------------:|:-----------------------
1_AGAVE.x     | February   |  training_set    | VEnron2\1027 | B3:F5          | ...
...           | ...        |  ...             | ...          | ...            | ...
