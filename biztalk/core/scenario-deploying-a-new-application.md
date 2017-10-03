---
title: "案例： 將新的應用程式部署 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, applications
- applications, deploying
- deploying [applications], examples
- applications, examples
- examples, deploying
ms.assetid: 6d34a626-9fd4-4c33-a067-b66333eec01f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 938767237d21b74829c786bdd5d57c7d9df15c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-a-new-application"></a>案例： 部署新的應用程式
本主題說明將應用程式部署至從未部署之新環境的實例，例如，將執行環境中設定的應用程式部署至實際執行環境。  
  
 中所述[應用程式部署程序](../core/the-application-deployment-process.md)，當您想要將應用程式從一個環境移到另一個，匯出至.msi 檔案的應用程式。 接著將 .msi 檔案匯入至新環境的 BizTalk 群組中。 您也可以在該群組中將會執行應用程式的電腦中安裝應用程式。 您必須先將應用程式安裝在即將執行的每部電腦中，並且啟動應用程式，應用程式才能開始運作。  
  
 在下列圖表中，Application1 會從 .msi 檔案匯入至 BizTalk 群組 B。  
  
 ![BizTalk 應用程式部署](../core/media/deployapplication.gif "DeployApplication")  
  
 這會將成品匯入至各種 BizTalk Server 資料庫，如下所示：  
  
-   BizTalk 組件、.NET 組件、繫結、繫結檔案、BAM 範本、COM 元件、憑證和文字檔案都會加入 BizTalk 管理資料庫。  
  
-   原則和詞彙會加入至「規則引擎」資料庫。  
  
-   BAM 範本和 BAM 定義檔案都會加入至「BAM 主要匯入」資料庫。  
  
 每個成品也會與 BizTalk 管理資料庫的 Application1 相關聯。  
  
 此應用程式也會在本機電腦中從 .msi 檔案進行安裝。 這會安裝 .msi 檔案中包含的各種成品，如下所示：  
  
-   在 Internet Information Services (IIS) Metabase 中建立名為 VirtualDirectory 的虛擬目錄。  
  
-   憑證會加入至本機憑證存放區。  
  
-   文字檔案和 COM 元件會複製到本機檔案系統。  
  
-   BizTalk 組件和 .NET 組件會加入至全域組件快取 (GAC) 中 (如果已針對這些組件選取這個部署選項)。  
  
-   .NET 組件和 COM 元件會加入至 Windows 登錄中 (如果已針對這些組件和元件選取這個部署選項)。  
  
## <a name="see-also"></a>另請參閱  
 [應用程式部署和管理案例](../core/application-deployment-and-management-scenarios.md)   
 [部署 BizTalk 應用程式](../core/deploying-biztalk-applications.md)