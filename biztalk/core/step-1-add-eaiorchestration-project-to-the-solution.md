---
title: 步驟 1： 將 EAIOrchestration 專案加入方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1c9aa0d9-2075-4c7e-8baf-1ecd2721859a
caps.latest.revision: 42
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3b8e2b9c197e01ed695311c67bc79cf5056c4d1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276862"
---
# <a name="step-1-add-eaiorchestration-project-to-the-solution"></a>步驟 1：將 EAIOrchestration 專案加入解決方案中
![步驟 4 之 1](../adapters-and-accelerators/adapter-oracle-ebs/media/step-1of4.gif "Step_1of4")  
  
 **若要完成的時間：** 5 分鐘  
  
 **目標：** 在此步驟中，您必須加入第二個專案到 EAI 方案。 然後新增協調流程至新專案。  
  
 **用途：** 建立協調流程的個別專案。 當有幾個不同的人在處理方案時，這是有所助益的。 您使用新協調流程自動化本課程的商務程序。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前必須先完成[第 1 課： 定義結構描述和對應](../core/lesson-1-define-schemas-and-a-map.md)。  
  
## <a name="procedures"></a>程序  
 如果您關閉[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]視窗中，請遵循 「 若要開啟 Visual Studio 專案 」 程序中[步驟 2： 建立庫存要求結構描述](../core/step-2-create-the-inventory-request-schema.md)加以開啟。  
  
#### <a name="to-add-another-project-to-your-solution"></a>新增另一個專案到您的方案  
  
1.  Visual Studio 中，從上**檔案**功能表上，指向**新增**，然後按一下 **新專案**。  
  
2.  在**新專案**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**已安裝的範本**|按一下**BizTalk 專案**，然後按一下 **空白 BizTalk Server 專案**。|  
    |**名稱**|輸入 `EAIOrchestration`。|  
    |**位置**|輸入 `C:\BTSTutorials\EAISolution`。|  
  
3.  按一下 **[確定]**。  
  
#### <a name="to-add-an-orchestration"></a>若要新增協調流程  
  
1.  在 方案總管 中，以滑鼠右鍵按一下**EAIOrchestration**，指向 **新增**，然後按一下 **新項目**。  
  
2.  在**加入新項目-EAIOrchestration**對話方塊方塊中，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**已安裝的範本**|按一下**協調流程檔案**，然後按一下  **BizTalk 協調流程**。|  
    |**名稱**|型別**EAIProcess.odx**。|  
  
3.  按一下 **[加入]**。  
  
     就會開啟「協調流程設計師」。 下圖顯示含有 EAIProcess 協調流程的「協調流程設計師」。  
  
     ![新的協調流程](../core/media/tut1-eaiprocess.gif "Tut1_EAIProcess")  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您已將第二個專案新增至 EAI 方案中。 然後在新專案中新增了協調流程。  
  
## <a name="next-steps"></a>後續步驟  
 定義商務程序中的[步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 定義商務程序](../core/step-2-define-the-business-process.md)   
 [步驟 3： 新增至協調流程連接埠](../core/step-3-add-ports-to-the-orchestration.md)   
 [步驟 4： 建置 EAIOrchestration 專案](../core/step-4-build-the-eaiorchestration-project.md)