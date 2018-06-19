---
title: 限制 BizTalk adapter for Oracle E-business Suite |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 149cee03-43cd-4cb3-a937-6565f5e96ce5
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e7611c56fbd24c7c7cf09d38d376df585b72b284
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22216270"
---
# <a name="limitations-of-biztalk-adapter-for-oracle-e-business-suite"></a>BizTalk adapter for Oracle E-business Suite 的限制
## <a name="general-limitations"></a>一般的限制  
 下列已知限制[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 XML 閘道、 進階佇列和商務事件。  
  
     不過，您可以避開商務事件限制以下列方式：  
  
    1.  在 Oracle 商務事件系統中，建立商務事件發生時叫用自訂的 PL/SQL 程序的訂閱。  
  
    2.  撰寫自訂的 PL/SQL 程序會接收商務事件。  
  
    3.  您可以使用自訂的 PL/SQL 程序，將儲存在資料表產生的資料 （事件和事件裝載）。  
  
    4.  使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢，或從資料表中接收通知。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 XML 型別。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含的欄位的記錄是否輸入 PL/SQL 資料表的記錄類型。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援複雜型別 （例如記錄類型，資料表類型、 UDT，以及 VARRAY） 內 BFILE 資料型別。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援巢狀只有最多兩個層級的 UDT。  
  
-   除了 PL/SQL 資料表[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援封裝內定義的 Udt。  
  
-   與 BizTalk Server 使用配接器，如果在 WCF 自訂認證的傳送埠不正確的不會處理要求訊息。 指定正確的認證之後，訊息傳送至 Oracle E-business Suite 和收到的回應。 不過，回應訊息不適用於輸出通訊埠。 在這種情況下，您可能需要重新啟動主控件執行個體。  
  
## <a name="limitations-due-to-odpnet"></a>由於 ODP.NET 限制  
 下列已知限制[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]基於 ODP.NET 限制：  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 PL/SQL 資料表未建立索引的數值欄位。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援不包含任何元素的關聯陣列。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含時間戳記資料類型，以本地時間區域屬性 (TimeStampLTZ) 的 Udt。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含 Udt"。" （句號） 在其名稱中。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 Udt，包含 BLOB、 CLOB、 和 NCLOB 資料類型做為 IN OUT 參數。  
  
-   [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。  
  
-   由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的資料錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
    -   BFILE  
  
    -   BLOB  
  
    -   CLOB  
  
    -   IntervalDS  
  
    -   IntervalYM  
  
    -   長整數  
  
    -   NCLOB  
  
    -   RowID  
  
    -   TimeStamp  
  
    -   TimeStampLTZ  
  
    -   TimeStampTZ  
  
## <a name="see-also"></a>另請參閱  
 [瞭解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)