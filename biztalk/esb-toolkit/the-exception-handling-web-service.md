---
title: "例外狀況處理的 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe6ebdf-9b92-40c7-93fb-afd6c5f68aaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8d8f3439e3b99d118e2932d0a158113ec51be2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-exception-handling-web-service"></a>例外狀況處理的 Web 服務
例外狀況處理的 Web 服務接受的錯誤訊息，並將其發佈至 ESB 例外狀況入口網站。 用戶端應用程式建立例外狀況訊息，並將其發行到 ESB，針對該例外狀況型別或泛型處理常式中，設定任何處理常式可以處理的例外狀況的地方。 此服務的主要優點是它可讓實體之外 ESB 應用程式參與 ESB 例外狀況處理機制。  
  
 [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含此服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。 服務名稱就是**ESB。ExceptionHandlingServices**和**ESB。ExceptionHandlingServices.WCF**分別和服務會公開單一方法：  
  
-   **SubmitFault**。 這個方法會採用的執行個體**FaultMessage**類別並沒有傳回值。  
  
 如需方法例外狀況處理機制的運作方式，請參閱[使用 ESB 例外狀況管理](../esb-toolkit/using-esb-exception-management.md)。  
  
> [!NOTE]
>  根據預設，例外狀況處理的 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。 您應該設定服務，讓需要 SSL 用戶端存取，並保護網際網路資訊服務 (IIS) Web 服務主機電腦和裝載的伺服器之間的連線**ESBExceptions**資料庫使用網路層級 IPSec 和適當的檔案層級存取控制清單 (ACL) 權限。