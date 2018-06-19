---
title: 應用程式部署工作 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- applications, deploying
- applications, tasks
- deploying [applications], tasks
ms.assetid: 8cb29292-9868-41fa-9f2c-d1c20dfdddbb
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed5dd5b2a15bd8408ee11934d7dd6274e81651b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230422"
---
# <a name="application-deployment-tasks"></a>應用程式部署工作
本節中的主題提供了下列與 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 應用程式部署程序的每一個階段有關之工作的詳細資料：  
  
1.  **開發。** 開發人員要從 BizTalk 應用程式中包含的 BizTalk 組件部署[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]開發電腦上執行。 這樣會自動建立應用程式，並將組件中所包含的成品填入其中。 成品是指組成 BizTalk 商務解決方案的所有項目，包括 BizTalk 組件、.NET 組件、結構描述、對應、繫結、憑證等等。 開發人員會在應用程式中加入任何其他的成品或是執行其他組態工作，即可完成應用程式的設定。 然後，開發人員會從 .msi 檔案安裝此應用程式、測試它來驗證功能、修正任何問題，然後從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將此應用程式匯出為 .msi 檔案。  
  
2.  **測試。** 測試人員會將.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦上執行測試，這樣會建立在應用程式[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 測試人員也會在主控件電腦上從 .msi 檔案安裝此應用程式。 當測試及 BUG 修正完畢後，測試人員會從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將此應用程式匯出為 .msi 檔案。  
  
3.  **預備環境。** IT 系統管理員會將.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]臨時伺服器上所執行的生產環境中設定它、 將它安裝在主機電腦上、 驗證其功能，然後將完成的應用程式匯出為.msi 檔案。  
  
4.  **生產環境。** IT 系統管理員會將.msi 檔案匯入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行在實際執行環境中，主機電腦上安裝應用程式，然後啟動 應用程式。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [BizTalk 應用程式部署的開發工作](../core/development-tasks-for-biztalk-application-deployment.md)  
  
-   [BizTalk 應用程式部署的測試工作](../core/testing-tasks-for-biztalk-application-deployment.md)  
  
-   [BizTalk 應用程式部署的預備工作](../core/staging-tasks-for-biztalk-application-deployment.md)  
  
-   [BizTalk 應用程式部署的實際執行工作](../core/production-tasks-for-biztalk-application-deployment.md)