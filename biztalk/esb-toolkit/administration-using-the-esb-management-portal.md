---
title: 使用 ESB 管理入口網站管理 |Microsoft Docs
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
ms.openlocfilehash: 24c44951b4284e0d17b2d8e69011cedfa213c219
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967759"
---
# <a name="administration-using-the-esb-management-portal"></a>使用 ESB 管理入口網站管理
ESB 管理入口網站中，包含[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，會示範如何使用計量和可能性在於擴充 BizTalk ESB 工具組範例網站。 在入口網站提供您可以用來建置您自己自訂的入口網站的起點。  
  
 ESB 管理入口網站也是高度有效且實用的工具，可協助最大化的使用和 ESB 例外狀況管理系統的效率。 此外，入口網站提供使用者介面為基礎的通用描述、 探索與整合 (UDDI) 登錄伺服器和稽核等功能的圖形化的組態功能檢視歷程記錄資訊設定警示和通知，以及讓使用者訂閱警示，表示在 ESB 應用程式中發生的錯誤。  
  
 本章節描述您可以使用 ESB 管理入口網站中，包括下列來完成常見工作：  
  
-   [使用例外狀況和錯誤訊息](../esb-toolkit/working-with-exceptions-and-fault-messages.md)  
  
-   [設定警示、通知和訂用帳戶](../esb-toolkit/configuring-alerts-notifications-and-subscriptions.md)  
  
-   [檢視和管理稽核和歷程記錄](../esb-toolkit/viewing-and-managing-auditing-and-history.md)  
  
-   [使用圖表和報告分析錯誤趨勢](../esb-toolkit/analyzing-fault-trends-using-charts-and-reports.md)  
  
-   [檢視和發佈 UDDI 註冊](../esb-toolkit/viewing-and-publishing-uddi-registrations.md)  
  
> [!NOTE]
>  ESB 管理入口網站的個別功能的詳細說明，請參閱 < [ESB 管理入口網站功能參考](../esb-toolkit/esb-management-portal-feature-reference.md)。  
  
## <a name="esb-portal-technologies"></a>ESB 入口網站的技術  
 ESB 管理入口網站會利用下列技術：  
  
- [!INCLUDE[btsSQLServerNoVersion_md](../includes/btssqlservernoversion-md.md)] 
  
- ASP.NET
  
- [Enterprise Library](http://go.microsoft.com/fwlink/?LinkId=188292) ([http://go.microsoft.com/fwlink/?LinkId=188292](http://go.microsoft.com/fwlink/?LinkId=188292))。 ESB 管理入口網站會使用下列的企業程式庫組件：  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Caching**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Common**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Data**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.ExceptionHandling.Logging**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Logging**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.ObjectBuilder2**  
  
  -   **Microsoft.Practices.EnterpriseLibrary.Validation**  
  
  -   Microsoft.Practices.Unity  
  
- [Microsoft Chart Controls](http://go.microsoft.com/fwlink/?LinkId=188293) (http://go.microsoft.com/fwlink/?LinkId=188293)適用於 Microsoft.NET Framework 4  
  
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]計量追蹤只會延伸到錯誤的例外狀況管理系統的追蹤。