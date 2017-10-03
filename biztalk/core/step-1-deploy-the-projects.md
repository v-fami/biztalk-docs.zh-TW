---
title: "步驟 1： 部署專案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: "44"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4262b2bb424a339f866f3b4a14ae03c2e507f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-deploy-the-projects"></a>步驟 1：部署專案
![步驟 3 之 1](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：**在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。  
  
 **用途：**當您部署專案或方案在 Visual Studio 中的時，自動建置並部署到指定的應用程式組件。 做為此程序的一部分，組件連同協調流程、結構描述，以及其所包含的對應 (稱為「成品」) 都會匯入到本機 BizTalk 管理資料庫，並會在資料庫中與指定的應用程式建立關聯。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前，您必須先完成下列課程：  
  
    -   [第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md)  
  
    -   [第 2 課： 定義商務程序](../core/lesson-2-define-the-business-process.md)  
  
-   您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分來登入。  
  
-   在支援使用者帳戶控制 (UAC) 的系統上，您必須使用系統管理權限來執行 Visual Studio。  
  
## <a name="procedures"></a>程序  
 若要使用 Visual Studio 來部署應用程式，您必須登入 Windows 成為 BizTalk Server 系統管理員群組的成員，然後以系統管理員的身分執行 Visual Studio。  否則，您會收到「拒絕存取」錯誤。  
  
#### <a name="to-open-the-solution-with-administrative-privileges"></a>若要使用系統管理權限來開啟方案  
  
1.  登入 Windows 成為 BizTalk Server 系統管理員群組的成員。  
  
2.  啟動**Microsoft Visual Studio**身為系統管理員。  
  
3.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。  
  
4.  在**開啟專案**對話方塊中，瀏覽至**EAISolution.sln**專案方案檔，然後按一下**開啟**。  
  
 部署程序要求組件必須是以強式名稱簽署的。  您必須藉由建立專案與強式名稱組件金鑰檔案的關聯，簽署您的組件。  此檔案是由教學課程檔案所提供。  
  
 BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。 BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。 我們可以指定專案的應用程式名稱。  此部署程序會自動建立具有指定名稱的新應用程式 (如果它不存在的話)。  
  
#### <a name="to-configure-and-deploy-the-projects"></a>若要設定和部署專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**EAISchemas**專案，然後再按一下**屬性**。  
  
2.  按一下**簽署**索引標籤上，選取**簽署組件**。  
  
3.  從下拉式清單中**選擇強式名稱金鑰檔**方塊中，選取**\<瀏覽 >**。  
  
4.  在**選取檔案**對話方塊方塊中，瀏覽至**C:\BTStutorials**，按一下  **btsTutorials.snk**，然後按一下 **開啟**。  
  
5.  按一下**部署** 索引標籤右邊的方塊**應用程式名稱**，型別`EAISolution`。  
  
6.  從下拉式清單中的清單右邊的方塊**重新部署**，選取**True**。  
  
7.  在 方案總管 中，以滑鼠右鍵按一下**EAISchemas**，然後按一下 **部署**。  此時，[輸出] 視窗應該會顯示：  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  重複步驟 1 到 7 來部署 EAIOrchestration 專案。  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。  
  
## <a name="next-steps"></a>後續步驟  
 您會建立實體連接埠，並將它們繫結至協調流程的邏輯連接埠。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md)   
 [步驟 3： 測試方案](../core/step-3-test-the-solution2.md)