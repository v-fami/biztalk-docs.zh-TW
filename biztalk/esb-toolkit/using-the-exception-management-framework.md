---
title: "使用例外狀況管理架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b69c9c01-e7e4-4788-8fe2-43d32075155d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47442604831a3a11bb9d00b65f9dc34961de2367
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-exception-management-framework"></a>使用例外狀況管理架構
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]動態轉換和路由，用來通訊失敗 （例如，未部署的對應或不會傳回對應名稱的規則） 的例外狀況。 當轉換或路由程序失敗時，ESB 建立例外狀況訊息，並將它提交至 Messagebox 資料庫的直接繫結連接埠。 ESB 也會實作名為所有的傳送埠。訂閱和擷取例外狀況訊息，並將其發行到 ESB 管理入口網站的例外狀況。  
  
 此外，所有的協調流程範例使用 ESB 無法協調流程例外狀況路由 API 來處理例外狀況。 您可以在任何您所部署的協調流程專案中使用此 API。 ESB 無法協調流程的例外狀況路由功能提供截獲並報告 BizTalk Server 環境中的所有例外狀況的標準方法。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例專案會示範如何使用 ESB 例外狀況管理架構。 下列兩個專案封裝 ESB 無法協調流程的例外狀況路由 API:  
  
-   **ESB。ExceptionHandling**。 此專案包含用於處理協調流程中的錯誤訊息處理的所有公用方法。 您必須在全域組件快取在本機伺服器上此專案中註冊組件。  
  
-   **ESB。ExceptionHandling.Schemas.Faults**。 此專案包含命名空間所定義的錯誤訊息結構描述**http://schemas.microsoft.biztalk.practices.esb.com/exceptionhandling**和系統屬性結構描述。 您必須將此專案部署至 Microsoft.Practices.ESB 應用程式容器中。  
  
 使用 ESB 無法協調流程的例外狀況路由 API 的所有專案必須都參考核心組件：  
  
-   **Microsoft.Practices.ESB.ExceptionHandling.dll**  
  
-   **Microsoft.Practices.ESB.ExceptionHandling.Schemas.Faults.dll**  
  
 下列各節提供有關使用 ESB 例外狀況管理架構的詳細資訊：  
  
-   [ESB 例外狀況應用程式開發介面成員](../esb-toolkit/the-esb-exception-api-members.md)  
  
-   [建立並發佈錯誤訊息](../esb-toolkit/creating-and-publishing-fault-messages.md)  
  
-   [訂閱和擷取訊息](../esb-toolkit/subscribing-to-and-extracting-messages.md)  
  
-   [實例解決方案的步驟](../esb-toolkit/scenario-solution-steps.md)