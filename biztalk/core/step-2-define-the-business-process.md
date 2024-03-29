---
title: 步驟 2： 定義商務程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b37bd9f1-5ee2-434d-950a-cf12967b6fc2
caps.latest.revision: 49
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 850b8b98764bc782dc62c6ebe792ace2d80ef0a8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998103"
---
# <a name="step-2-define-the-business-process"></a>步驟 2：定義商務程序
![步驟 4 之 2](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")  
  
 **若要完成的時間：** 8 分鐘  
  
 **目標：** 在此步驟中，您必須使用協調流程設計師來定義商務程序。  
  
 **用途：** 協調流程的工作流程代表及自動化您的公司核准庫存補充要求的商務程序。  
  
## <a name="prerequisites"></a>必要條件  
 開始此步驟之前，請注意下列需求：  
  
-   在開始此步驟之前必須先完成[步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md)。  
  
## <a name="procedures"></a>程序  
 開發協調流程的第一個步驟是使用動作圖形來表示商務程序。  
  
#### <a name="to-create-the-eai-business-process-workflow"></a>建立 EAI 商務程序工作流程  
  
1. 從 Visual Studio，在 [方案總管] 中，按兩下**EAIProcess.odx**開啟協調流程。  
  
2. 在協調流程設計師中，從協調流程工具箱拖曳**接收**圖形，並將它之間放**開始**（綠色圓形） 和**結束**（紅色八角形） 圖形。  
  
   > [!NOTE]
   >  如果無法開啟，請在 [工具箱]**檢視**功能表上，按一下**工具箱**。 若要將它錨定在畫面上，請按一下圖釘圖示。  
  
3. 從 [工具箱] 拖曳**決定**[接收] 圖形下方的圖形。  
  
4. 從 [工具箱] 拖曳**轉換**「 決定 」 圖形的左邊分支的圖形。 [轉換] 圖形會以巢狀結構位於 [建構訊息] 圖形內。  
  
5. 從 [工具箱] 拖曳**傳送**[轉換] 圖形下方的圖形。  
  
6. 從 [工具箱] 拖曳**傳送**圖形以 「 決定 」 圖形的右邊分支。  在您新增動作圖形之後，協調流程看起來就像下面一樣：  
  
    ![EAI 程序](../core/media/eaiprocess.gif "EAIProcess")  
  
   下一個步驟是定義訊息變數。  幾個動作圖形有一個需要指定的訊息屬性。  
  
#### <a name="to-define-message-variables"></a>若要定義訊息變數  
  
1.  從 Visual Studio 中，按一下**檢視**功能表上，按一下**其他 Windows**，然後按一下**協調流程檢視**。  
  
2.  從協調流程 檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
3.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**識別碼**|型別**RequestMessage**。|  
    |**訊息類型**|按一下 **結構描述**，然後按一下**\<選取 從參考組件...\>**. 從 [選取成品類型] 視窗中，按一下**EAISchemas**，然後按一下**要求**。 按一下 **[確定]**。|  
  
4.  從協調流程 檢視中，以滑鼠右鍵按一下**訊息**，然後按一下**新訊息**。  
  
5.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**識別碼**|型別 **[requestdeclinemessage]**。|  
    |**訊息類型**|按一下 **結構描述**，然後按一下**\<選取 從參考組件...\>**. 從 [選取成品類型] 視窗中，按一下**EAISchemas**，然後按一下**拒絕**。 按一下 **[確定]**。|  
  
#### <a name="to-configure-the-properties-of-the-shapes"></a>若要設定圖案的屬性  
  
1.  在設計介面上，按一下**接收**圖形加以選取。  
  
2.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**ReceiveRequest**。|  
    |**Message**|選取  **RequestMessage**。|  
    |**Activate**|從下拉式清單中，選取 **，則為 True**。|  
  
    > [!NOTE]
    >  如果 屬性 視窗未開啟，請在**檢視**功能表上，按一下**屬性 視窗**。  
  
3.  在設計介面上，按一下**決定**圖形。  
  
4.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**CheckGrandTotal**。|  
  
    > [!NOTE]
    >  如果 屬性 視窗未開啟，請在**檢視**功能表上，按一下**屬性 視窗**。  
  
5.  在設計介面上，按一下**Rule_1**圖形。  
  
6.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**DeclineRule**。|  
    |**運算式**|按一下省略符號 (**...**)，然後輸入`RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`。 按一下 [確定] 。|  
  
7.  在設計介面上，按一下 **[constructmessage_1]** 圖形。  
  
8.  在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**ConstructRequestDeclineMessage**。|  
    |**建構的訊息**|選取  **requestdeclinemessage**。|  
  
9. 在設計介面上，按一下 **[transform_1]** 圖形。  
  
10. 在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**TransformRequestToRequestDeclineMessage**。|  
    |**對應名稱**|按一下  **...**. 從 [轉換組態] 中，執行下列動作：<br /><br /> 輸入組態資訊：<br /><br /> -按一下**現有的對應**。<br /><br /> 完整格式的對應名稱：<br /><br /> -選取**\<選取 從參考組件\>**。  從左窗格中，選取**EAISchemas**。  從右窗格選取 [EAISchemas.MapToReqDecline]。  按一下 [確定] 。<br /><br /> 來源<br /><br /> -RequestMessage<br /><br /> 目的地<br /><br /> -[Requestdeclinemessage]|  
  
11. 在設計介面上，按一下**Send_1**圖形。  
  
12. 在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**SendRequestDecline**。|  
    |**Message**|選取  **requestdeclinemessage**。|  
  
13. 在設計介面上，按一下 **[send_2]** 圖形。  
  
14. 在 [屬性] 視窗中，執行下列步驟：  
  
    |使用|以進行此動作|  
    |--------------|----------------|  
    |**名稱**|型別**SendRequestToERP**。|  
    |**Message**|選取  **RequestMessage**。|  
  
## <a name="what-did-i-just-do"></a>我剛剛做了什麼？  
 在此步驟中，您使用「協調流程設計師」定義了商務程序。  
  
## <a name="next-steps"></a>後續步驟  
 中的協調流程中加入邏輯連接埠[步驟 3： 新增協調流程連接埠](../core/step-3-add-ports-to-the-orchestration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 1： 將 EAIOrchestration 專案加入方案](../core/step-1-add-eaiorchestration-project-to-the-solution.md)   
 [步驟 3： 新增連接埠至協調流程](../core/step-3-add-ports-to-the-orchestration.md)   
 [步驟 4：建置 EAIOrchestration 專案](../core/step-4-build-the-eaiorchestration-project.md)