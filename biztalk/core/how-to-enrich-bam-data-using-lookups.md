---
title: 如何修飾 BAM 資料使用查閱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BAM, data lookups
ms.assetid: 8d10659e-97d6-4cd1-9b4d-307afd43c763
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43b42b42158bc3b3c179d624340a97a890072a17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-enrich-bam-data-using-lookups"></a>如何利用查閱修飾 BAM 資料
有時候，作業期間所提供的資料不盡然包含報表所需的一切。 例如，執行階段可能只提供 ProductID (產品識別碼) 卻沒有 ProductName (產品名稱)。 由於 BAM 活動代表的是與資料實際收集方式無關的抽象概念，活動理應如同報表最終呈現的資料也包含 "ProductName" 項目。 就像任何其他項目，您可以將此項目納入里程碑群組、持續時間、維度和量值等說明性質的概念中。 由於執行階段並未提供 ProductName，您必須額外取得足以執行查閱的若干資料，例如 ProductID。  
  
 您應該收集同一個資料行的資料，而非報表實際需要的資料。 例如，在執行階段應該收集 ProductID 而非 ProductName。 如果還需要其他資料行，請在活動中建立其他項目，但切勿在任何檢視上使用這些項目。  
  
### <a name="to-enrich-bam-data-via-lookups"></a>利用查閱修飾 BAM 資料  
  
1.  部署 BAM 定義。  
  
2.  在 SQL Server Management Studio 中，新增含有所需資料的伺服器做為遠端伺服器。  
  
3.  找到名為 BAM_AN_`<View Name>` 的資料分析封裝。 以 SalesMgr 檢視為例，封裝的名稱即為 BAM_AN_SalesMgr。  
  
4.  設定顯示比例，將封裝的檢視放大 (譬如 100%)。  
  
5.  新增要在查閱中使用的 SQL 連線。  
  
6.  找到位於「清理階段」步驟之後的轉換資料工作。 此處代表將資料從 PrimaryImport 移到 StarSchema 資料庫。 有兩個執行個體的這項工作 — 一個適用於已完成的活動，而另一個進行中。 請將其餘所有步驟套用至這兩個工作。  
  
7.  按一下轉換。  
  
8.  選取 [查閱]；使用查閱連接新增 "LookupProductByID" 查閱 (請參閱《SQL 線上叢書》以瞭解何謂查閱)。 例如，如果查閱是只含有 ProductID 和 ProductName 資料行的 "LookupProduct" 資料表，查閱的文字即為：  
  
    ```  
    SELECT ProductName  
    FROM   LookupProduct  
    WHERE ProductID=?  
    ```  
  
9. 按一下 [轉換] 索引標籤。刪除預設的資料轉換 "Transform"，再另外建立 ActiveX 轉換。 按一下 [來源資料行]，然後加入所有的資料行。 按一下 [目的地資料行]，然後加入所有的資料行。  
  
10. 按一下 [一般] 索引標籤，再按一下 [屬性]。 這樣就會自動產生執行一般複製轉換的指令碼，如下所示：  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("ProductName") = DTSSource("ProductName")  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
11. 依照下列方式，使用查閱變更其值：  
  
    ```  
    Function Main()  
       ...  
       DTSDestination("Product")= _  
                      DTSLookups( "LookupProductByID" ).Execute(  _                                  DTSSource("Product"))  
       ...  
       Main = DTSTransformStat_OK  
    End Function  
    ```  
  
12. 儲存後執行封裝。  
  
13. 確定最終的 OLAP Cube 包含正確的資料。 請將封裝另存為 VBScript 或結構化儲存體檔案，因為封裝中除了 BAM 自動產生的步驟外，還包含您所自訂的程式碼。  
  
> [!NOTE]
>  查閱僅適用於透過 DTS 和 OLAP 所執行的排程報表。 如果您還需要其他資料，而非僅限於即時彙總所收集的資料，則必須先擷取資料再呼叫 BAM API。  
  
## <a name="see-also"></a>另請參閱  
 [使用商務活動監控](../core/using-business-activity-monitoring.md)   
 [部署當地語系化的 BAM XML 檔案](../core/deploying-localized-bam-xml-files.md)