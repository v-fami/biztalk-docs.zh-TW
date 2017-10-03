---
title: "開發 BizTalk 應用程式使用 SQL 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5471f28e-bce1-4295-b56d-954690e60749
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9963764a298246c5a236d10b6010feee8497278f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="develop-biztalk-applications-using-the-sql-adapter"></a>開發 BizTalk 應用程式使用 SQL 配接器
建立 BizTalk 專案中的開發 BizTalk 應用程式牽涉到[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]和使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]產生 XML 結構描述。 一旦您已經產生結構描述，您可以使用以內容為基礎的路由 (CBR)，或建立 BizTalk 協調流程傳送和接收符合產生結構描述的訊息。  
  
 CBR 可用在案例中傳送到 SQL Server 的訊息不需要任何大量的處理。 例如，如果您知道接收埠將會接收僅特定類型的訊息，您可以加入篩選條件要比對傳送埠的篩選運算式的路由傳送訊息的傳送埠。  
  
 在 BizTalk 協調流程，建立傳送和接收埠以傳送和接收訊息的[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，這會將訊息傳送至[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。 本節提供使用 BizTalk 協調流程使用 SQL Server 上執行作業的相關資訊[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。 [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]接著會採用[!INCLUDE[wcfadapter_short](../../includes/wcfadapter-short-md.md)]，它可以與 WCF 繫結互動。  
  
> [!IMPORTANT]
>  若要使用[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，您都必須設定**EnableBizTalkCompatibilityMode**內容繫結至**True**。 如需如何設定繫結屬性的資訊，請參閱[設定 SQL 配接器的繫結屬性](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [若要建立使用 SQL 配接器的 SQL 應用程式的必要條件](../../adapters-and-accelerators/adapter-sql/prerequisites-to-create-sql-applications-using-the-sql-adapter.md) 
  
-   [開發 BizTalk 應用程式與 SQL 配接器的建置組塊](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md) 
  
-   [Insert、 Update、 Delete 和選取資料表和檢視表與 SQL 配接器的作業](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md)  
  
-   [使用 SQL 配接器的大型資料類型執行資料表和檢視表上的作業](../../adapters-and-accelerators/adapter-sql/run-operations-on-tables-and-views-with-large-data-types-using-the-sql-adapter.md)  
  
-   [使用 BizTalk Server 的執行 SQL Server 中的預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-in-sql-server-using-biztalk-server.md)  
  
-   [執行具有單一 XML 參數的預存程序](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-with-a-single-xml-parameter-in-sql-using-biztalk.md)  
  
-   [執行預存程序具有 FOR XML 子句中使用 BizTalk server 的 SQL Server](../../adapters-and-accelerators/adapter-sql/execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk.md)  
  
-   [使用 BizTalk Server 來執行 SQL Server 上的複合作業](../../adapters-and-accelerators/adapter-sql/run-composite-operations-on-sql-server-using-biztalk-server.md)  
  
-   [使用 BizTalk Server 叫用 SQL Server 中的純量函式](../../adapters-and-accelerators/adapter-sql/invoke-scalar-functions-in-sql-server-using-biztalk-server.md)  
  
-   [使用 BizTalk Server 叫用 SQL Server 中的資料表值函式](../../adapters-and-accelerators/adapter-sql/invoke-table-valued-functions-in-sql-server-using-biztalk-server.md) 
  
-   [使用 BizTalk Server 執行 ExecuteReader、 ExecuteScalar 或 ExecuteNonQuery 作業](../../adapters-and-accelerators/adapter-sql/executereader-executescalar-or-executenonquery-in-sql-server-using-biztalk.md)  
  
-   [輪詢 SQL Server 與 BizTalk Server 使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)  
  
-   [使用 BizTalk Server 接收 SQL 查詢通知](../../adapters-and-accelerators/adapter-sql/receive-sql-query-notifications-using-biztalk-server.md)  
  
## <a name="see-also"></a>另請參閱  
[開發 SQL 應用程式](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)