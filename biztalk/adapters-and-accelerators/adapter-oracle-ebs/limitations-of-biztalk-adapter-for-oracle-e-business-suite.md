---
title: BizTalk Adapter for Oracle E-business Suite 的限制 |Microsoft Docs
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
ms.openlocfilehash: b6de75a2955632f4f8e0daae2a2035e90f1f2fca
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988391"
---
# <a name="limitations-of-biztalk-adapter-for-oracle-e-business-suite"></a>BizTalk Adapter for Oracle E-business Suite 的限制
## <a name="general-limitations"></a>一般限制  
 下列已知限制[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]:  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援 XML 閘道 」、 「 進階佇列，和 「 商務事件。  
  
   不過，您可以以下列方式取得解決商務事件限制：  
  
  1. 在 Oracle 商務事件系統中，建立商務事件發生時叫用自訂的 PL/SQL 程序的訂用帳戶。  
  
  2. 撰寫自訂的 PL/SQL 程序會接收商務事件。  
  
  3. 您可以使用自訂的 PL/SQL 程序，在資料表中儲存產生的資料 （事件和事件裝載）。  
  
  4. 使用[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢，或從資料表中接收通知。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援的 XML 型別。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不會啟用用戶端設定為 NULL 的 VARRAY 中的第一個元素的值。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]執行不支援包含的欄位的記錄類型的記錄類型的 PL/SQL 資料表。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援具有循環參考的使用者定義型別 (Udt)。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援複雜類型 （例如記錄類型、 資料表類型、 UDT 和 VARRAY） 內的 BFILE 資料型別。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]支援巢狀只有最多兩個層級的 UDT。  
  
- PL/SQL 資料表，除了[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援封裝內定義的 Udt。  
  
- 當與 BizTalk Server 使用配接器，如果認證 wcf-custom 傳送埠不正確的時不會處理要求訊息。 您指定正確的認證之後，將訊息傳送到 Oracle E-business Suite 和收到的回應。 不過，回應訊息不適用於輸出連接埠。 在此情況下，您可能需要重新啟動主控件執行個體。  
  
## <a name="limitations-due-to-odpnet"></a>由於 ODP.NET 的限制  
 下列已知限制[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]由於 ODP.NET 的限制：  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援未編製索引為數值欄位的 PL/SQL 資料表。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援不包含任何元素的關聯陣列。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含當地時間區域屬性 (TimeStampLTZ) 的時間戳記資料類型的 Udt。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含 Udt"。" （句號） 在其名稱中。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]不支援包含 BLOB、 CLOB、 和 NCLOB 資料類型為在 OUT 參數的 Udt。  
  
- [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] Nepodporuje Varray 的下列簡單型別的 Varray: BFILE、 IntervalDS、 IntervalYM、 TimeStampLTZ 和 TimeStampTZ。  
  
- 由於關聯陣列的限制，PL/SQL 資料表或包含下列資料類型的任何記錄的 PL/SQL 資料表中不支援[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]:  
  
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
 [了解 BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)