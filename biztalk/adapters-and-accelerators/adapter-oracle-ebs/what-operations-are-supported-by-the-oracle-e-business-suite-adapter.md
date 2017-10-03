---
title: "Oracle E-business Suite 配接器支援哪些作業 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64cd124a-5e7f-4ee8-85d3-f9540b25d766
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7236c21f1e298f2ccd4cbb97db481cbd3626d186
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-operations-are-supported-by-the-oracle-e-business-suite-adapter"></a>Oracle E-business Suite 配接器支援哪些作業
## <a name="overview"></a>概觀
配接器用戶端可以根據 Oracle E-business Suite 中執行作業：  
  
-   建立 BizTalk 專案  
  
-   使用 WCF 通道模型  
  
-   使用 WCF 服務模型  
  
 [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]會公開應用程式可以在其上叫用，接著，可以呼叫應用程式上的作業。 這些作業會叫用透過通道傳送 SOAP 訊息。 如果需要回應，它會傳回 SOAP 訊息中透過相同的通道。 訊息結構和與每個作業相關聯的 SOAP 動作的相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。  
  
 本章節提供支援在使用 Oracle E-business Suite 作業的相關資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定應用程式內容](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md)  
  
-   [介面在資料表和檢視介面上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-interface-tables-and-interface-views.md)  
  
-   [PL/SQL 應用程式開發介面作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-pl-sql-apis.md)  
  
-   [並行程式的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-concurrent-programs.md)  
  
-   [要求的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-request-sets.md)  
  
-   [介面資料表、 介面檢視、 資料表和檢視表包含 LOB 資料的作業](../../adapters-and-accelerators/adapter-oracle-ebs/read-and-update-on-interface-tables-and-views-with-large-object-data-types.md)  
  
-   [資料表包含 BFILE 資料型別上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-tables-that-contain-bfile-data-types.md)  
  
-   [函式和預存程序的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-stored-procedures1.md)  
  
-   [函式和有 REF CURSOR 參數的程序的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-ref-cursor-parameters1.md)  
  
-   [函數和程序的記錄類型的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-functions-and-procedures-with-record-types1.md)  
  
-   [在同義字上的作業](../../adapters-and-accelerators/adapter-oracle-ebs/operations-on-synonyms2.md)  
  
-   [接收資料庫變更通知的考量](../../adapters-and-accelerators/adapter-oracle-database/before-you-receive-database-change-notifications-using-the-oracle-db-adapter.md)  
  
-   [使用輪詢進行傳入呼叫時的支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-inbound-calls-using-polling.md)  
  
-   [ExecuteNonQuery、 ExecuteReader 和 ExecuteScalar 作業的支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-executenonquery-executereader-and-executescalar-operations.md)  
  
-   [複合作業的支援](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-composite-operations2.md)  
  
-   [支援的 Oracle 使用者定義型別](../../adapters-and-accelerators/adapter-oracle-ebs/support-for-oracle-user-defined-types2.md)  
  
## <a name="see-also"></a>另請參閱  
[瞭解 BizTalk Adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/understand-biztalk-adapter-for-oracle-e-business-suite.md)