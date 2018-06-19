---
title: 管理使用 ESB 管理入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 478d1dcc-e9b2-443b-be98-5b7545322401
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 351d06df4d6384607564778c4b86d8c509379488
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290270"
---
# <a name="administration-using-the-esb-management-portal"></a>使用 ESB 管理入口網站的系統管理
ESB 管理入口網站中，包含[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，會示範如何使用計量，以及可能存在的值來擴充 BizTalk ESB Toolkit 的範例網站。 入口網站提供的起點，您可以從中建立您自己的自訂入口網站。  
  
 ESB 管理入口網站也是高度能夠且有用的工具，可協助最大化的使用方式和 ESB 例外狀況管理系統的效率。 此外，入口網站提供使用者介面為基礎的通用描述、 探索與整合 (UDDI) 登錄伺服器圖形化設定功能的功能，例如稽核，檢視記錄資訊設定警示和通知，以及讓使用者訂閱警示指出 ESB 應用程式中發生的錯誤。  
  
 本章節描述您可以完成使用 ESB 管理入口網站中，包括下列的一般工作：  
  
-   [使用例外狀況和錯誤訊息](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [設定警示、 通知和訂用帳戶](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [檢視及管理稽核和記錄](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [使用圖表和報告的錯誤趨勢分析](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [檢視與發行 UDDI 登錄](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  ESB 管理入口網站的個別功能的詳細說明，請參閱[ESB Management 入口網站功能參考](../esb-toolkit/esb-management-portal-feature-reference.md)。  
  
## <a name="esb-portal-technologies"></a>ESB 入口網站的技術  
 ESB 管理入口網站會利用下列技術：  
  
-   [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
-   ASP.NET
  
-   [Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292))。 ESB 管理入口網站會使用下列的企業程式庫組件：  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Caching**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Common**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Data**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Logging**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**  
  
    -   **Microsoft.Practices.EnterpriseLibrary.Validation**  
  
    -   Microsoft.Practices.Unity  
  
-   [Microsoft 圖表控制項](http://go.microsoft.com/fwlink/?LinkId=188293)(http://go.microsoft.com/fwlink/?LinkId=188293) 的 Microsoft.NET Framework 4  
  
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]度量追蹤只會延伸到錯誤追蹤的例外狀況管理系統。