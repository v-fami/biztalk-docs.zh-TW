---
title: 教學課程： 整合 BizTalk Server 2013 與 Salesforce |Microsoft Docs
description: 使用服務匯流排與 BIzTalk Server 與 Salesforce 整合
ms.custom: ''
ms.date: 12/07/2015
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06c9ae51-3f48-4086-883b-ab4d5b6e62e3
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aecf9bcd1ef29a1324dc1b040388f17a19a71c52
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011727"
---
# <a name="tutorial-integrating-biztalk-server-2013-with-salesforce"></a>教學課程： 整合 BizTalk Server 2013 與 Salesforce
校稿者： [Nick Hauenstein](http://social.msdn.microsoft.com/profile/nick.hauenstein/)， [、 Steef-jan Wiggers](http://social.msdn.microsoft.com/profile/steef-jan%20wiggers)  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 導入了一些新的配接器可進行混合式案例，涉及內部部署和 Azure 技術。 在此教學課程中，我們會了解如何使用新的配接器和 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來整合單純的雲端實體，像是 Salesforce 與內部部署 [!INCLUDE[winazure](../includes/winazure-md.md)] 進行整合。 開始之前，讓我們先了解透過與 Salesforce 整合的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所達成的商務目標。  
  
 我們也能建立包括 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 Salesforce 以及舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的混合式方案；然而，該方案包括了透過使用 Web 服務 (SOAP) 和 Salesforce 整合，因此更加複雜。 透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和新的配接器，會讓方案簡單許多。  
  
## <a name="business-scenario"></a>商務案例  
 Northwind 使用 Salesforce 線上 CRM 系統做為方案，以透過準銷售案源追蹤客戶。 每當在 Salesforce 系統中建立了商機時，Northwind 會希望能夠通知自己的內部部署系統，例如 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，以便讓其他下遊的系統能抓取相關資料並開始進行其他相關的處理程序。 Northwind 計劃使用可透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 取用的新配接器實作此方案，並包含部份 [!INCLUDE[winazure](../includes/winazure-md.md)] 元件。 方案中的端對端資料流看起來如下：  
  
- 業務代表會在 Salesforce 系統中建立一個「商機」。  
  
- 當商機狀態設為 "Closed Won" 時，會傳送通知到 [!INCLUDE[winazure](../includes/winazure-md.md)] 上裝載的轉送端點。  
  
- 使用新的 WCF-BasicHttpRelay 配接器，會將通知資訊傳至含有內部部署的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統。  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用接收到的資訊做為通知的一部份、叫用 Salesforce 中的 REST 端點、使用新的 WCF-WebHttp 配接器並取得商機的詳細資訊。  
  
- 最後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用從 Salesforce 收到的資訊，在內部 SQL Server 資料庫表格中建立一個訂單項目。  
  
  以上是您必須執行的步驟集，才能達成本方案中說明的整合目標。 每個步驟都包含廣泛的活動集，當我們在建立方案時會看見。  
  
  這裡是描述端對端整合方案的說明：  
  
  ![BizTalk Server 和 Salesforce 的整合案例](../core/media/bts-sf-scenario.gif "BTS_SF_Scenario")  
  
## <a name="prerequisites"></a>必要條件  
 您必須先設定此解決方案的電腦上安裝下列軟體：  
  
- [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]  
  
- [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]  
  
- [!INCLUDE[afproductnameshort](../includes/afproductnameshort-md.md)]  
  
- [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]  
  
  您必須擁有下列服務訂用帳戶：  
  
- [!INCLUDE[winazure](../includes/winazure-md.md)] 訂閱  
  
- Salesforce Developer Edition 帳戶  
  
## <a name="more-resources"></a>其他資源  
 除了本教學課程中，您也可以查看下列資源以深入了解整合[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用新的配接器中導入的 Salesforce [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
- 虛擬實驗室示範[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]且可在 Salesforce 的整合[ http://go.microsoft.com/fwlink/?LinkId=290930 ](http://go.microsoft.com/fwlink/?LinkId=290930)。  
  
- 本教學課程為基礎的範例是下載[ http://go.microsoft.com/fwlink/?LinkId=290932 ](http://go.microsoft.com/fwlink/?LinkId=290932)。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [步驟 1：建立服務匯流排命名空間](../core/step-1-create-a-service-bus-namespace.md)  
  
-   [步驟 2：設定 Salesforce 系統](../core/step-2-set-up-the-salesforce-system.md)  
  
-   [步驟 3：在 Visual Studio 中建立 BizTalk Server 解決方案](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)  
  
-   [步驟 4：設定 BizTalk Server 解決方案](../core/step-4-configure-the-biztalk-server-solution.md)  
  
-   [步驟 5：測試解決方案](../core/step-5-test-the-solution.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 教學課程](../core/biztalk-server-tutorials.md)