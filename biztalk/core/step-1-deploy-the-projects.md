---
title: 步驟 1： 部署專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: 44
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad4424327f6cd24624abe6b4a850f3c24153e6a4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974120"
---
# <a name="step-1-deploy-the-projects"></a>步驟 1：部署專案
![步驟 3 之 1](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您部署了 EAISchemas 與 EAIOrchestration 專案。  
  
 **用途：** 當您部署專案或方案在 Visual Studio 中的時，自動建置並部署到指定的應用程式組件。 做為此程序的一部分，組件連同協調流程、結構描述，以及其所包含的對應 (稱為「成品」) 都會匯入到本機 BizTalk 管理資料庫，並會在資料庫中與指定的應用程式建立關聯。  
  
## <a name="prerequisites"></a>必要條件  
  
-   [課程 1：定義結構描述及對應](../core/lesson-1-define-schemas-and-a-map.md)  
  
-   [課程 2：定義商務程序](../core/lesson-2-define-the-business-process.md)  
  
-   成員的身分登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組

-   以系統管理權限執行 Visual Studio

> [!TIP]
> 您可以下載必要的教學課程檔案在[教學課程 1： 企業應用程式整合](https://www.microsoft.com/download/details.aspx?id=22793)。

## <a name="open-the-solution-with-administrative-rights"></a>以系統管理權限開啟的方案  
  
1.  BizTalk Server 系統管理員群組的成員身分登入 Windows。  
  
2.  啟動**Microsoft Visual Studio**身為系統管理員。  
  
3.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]上**檔案**功能表上，指向**開啟**，然後按一下 **專案/方案**。  
  
4.  在**開啟專案**對話方塊中，瀏覽至**EAISolution.sln**專案方案檔，然後按一下**開啟**。  
  
 部署程序要求組件必須是以強式名稱簽署的。  您必須藉由建立專案與強式名稱組件金鑰檔案的關聯，簽署您的組件。  教學課程檔案中包含此檔案。  
  
 BizTalk 應用程式是 BizTalk Server 的其中一項功能，能讓 BizTalk Server 商務解決方案的部署、管理和疑難排解更加快速輕鬆。 BizTalk 應用程式是 BizTalk Server 商務解決方案中所使用項目 (稱為「成品」) 的邏輯群組。 我們可以指定專案的應用程式名稱。  部署程序會自動建立新的應用程式具有指定的名稱，如果不存在。  
  
## <a name="configure-and-deploy-the-projects"></a>設定和部署專案  
  
1.  在 [方案總管] 中，以滑鼠右鍵按一下**EAISchemas**專案，然後再按一下**屬性**。  
  
2.  按一下**簽署**索引標籤上，選取**簽署組件**。  
  
3.  從下拉式清單中**選擇強式名稱金鑰檔**方塊中，選取**\<瀏覽...\>**.  
  
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
  
 [步驟 2： 設定並啟動應用程式](../core/step-2-configure-and-start-the-application1.md)   
 [步驟 3：測試解決方案](../core/step-3-test-the-solution2.md)
