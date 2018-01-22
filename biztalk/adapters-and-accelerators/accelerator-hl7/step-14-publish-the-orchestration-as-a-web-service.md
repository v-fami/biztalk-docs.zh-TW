---
title: "步驟 14： 發佈為 Web 服務的協調流程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, publishing
- publishing, orchestrations
- Web services, orchestrations
- message enrichment tutorial, orchestrations
- publishing, Web services
- message enrichment tutorial, Web services
ms.assetid: 8f29a7be-a679-4ca6-a648-35338d9e9e98
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c742d21dd2f2e1d95f697beea3d5d5dfa0461d2
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="step-14-publish-the-orchestration-as-a-web-service"></a>步驟 14： 發佈為 Web 服務的協調流程
在此步驟中，您可以使用 BizTalk Web 服務發佈精靈發佈為 Web 服務協調流程。  
  
 之前協調流程發佈為 Web 服務，您必須確保確認 BizTalkServerIsolatedHost 的登入帳戶屬於 BizTalk 外掛式主控件使用者群組，使其具有 BizTalk 資料庫的存取權。 這是必要的因為 SOAPReceivePort 接收位置在此教學課程 Web 服務發佈精靈所建立的接收處理常式會是 BizTalkServerIsolatedHost，不是 BizTalkServerApplication。 接收處理常式會是 BizTalkServerIsolatedHost 因為 SOAP 配接器是 IIS 處理序，而非 BizTalk 處理序下執行。  
  
### <a name="to-ensure-access-privileges-for-the-soapreceiveport-receive-location"></a>若要確保能存取 SOAPReceivePort 權限接收位置  
  
1.  在 BizTalk Server 管理主控台，在**主控件執行個體**中**平台設定**] 節點，以滑鼠右鍵按一下**BizTalkServerIsolatedHost**，然後按一下 [ **屬性**。 在 屬性 對話方塊中，按一下 **設定**。 請注意**登入**帳戶。  
  
2.  在 [電腦管理] 對話方塊底下**群組**中**本機使用者和群組**節點中，按兩下**BizTalk Isolated Host Users**。 如果登入帳戶**BizTalkServerIsolatedHost**不是成員的**BizTalkServerIsolatedHost**，新增至群組。  
  
### <a name="to-run-the-biztalk-web-services-publishing-wizard"></a>若要執行 BizTalk Web 服務發佈精靈  
  
1.  在 方案總管的 Visual Studio 中，按一下 **方案 'BTAHL7V22Common'**。 在**工具**功能表上，按一下  **BizTalk Web 服務發佈精靈**。  
  
2.  在**BizTalk Web 服務發佈精靈**上** 褖畫惎**頁面上，按一下**下一步**。  
  
3.  在 **建立 Web 服務** 頁面上，選取 **BizTalk 協調流程發佈為 web 服務**, ，然後按一下  **下一步**。  
  
4.  在**BizTalk 組件**頁面上，於**BizTalk 組件檔案 (\*.dll)**欄位中，瀏覽或輸入 **\<*磁碟機*\>: \Tutorial\BTAHL7V22Common\BTAHL7 Project\bin\development**，按一下  **BTAHL7 Project.dll**，按一下 **開啟**，然後按一下 **下一步**.  
  
5.  在**協調流程和連接埠**頁面上，確定所有節點都已選取，然後按一下 **下一步**。  
  
6.  上**Web 服務屬性**] 頁面上，針對**web 服務目標命名空間**，型別**http://localhost**，然後按一下 [**下一步**。  
  
7.  在**Web 服務專案**頁面上，選取**允許匿名存取 web 服務**和**建立 BizTalk 接收位置，在下列應用程式中**。 選取**BizTalk Application 1**應用程式。 保留預設值**位置**欄位。 按一下**下一步**接受預設專案位置。  
  
8.  在**Web 服務專案摘要**頁面上，按一下**建立**產生 ASP.NET Web 服務專案。  
  
9. 按一下 **[完成]** 關閉精靈。  
  
10. BizTalk Server 관리 콘솔을 엽니다. 在主控台中，展開  **BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開**BizTalk Application 1**.  
  
11. 按一下**接收位置**，以滑鼠右鍵按一下**WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**，然後按一下 **屬性**.  
  
12. 在 [接收位置屬性] 對話方塊中，按一下**接收管線**，選取**Microsoft.BizTalk.DefaultPipelines.XMLReceive**從下拉式清單，然後按一下**確定**.  
  
13. 以滑鼠右鍵按一下**WebService_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**，然後按一下 **啟用**。  
  
 若要繼續[步驟 15： 設定傳送埠和接收埠](../../adapters-and-accelerators/accelerator-hl7/step-15-configure-the-send-and-receive-ports.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)