---
title: 工作 4： 設定建構訊息 Shape1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3e66a9d-c549-42d0-849b-9e1744056429
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f781e03f83223f7d82628ee9c01728a0754b149f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278206"
---
# <a name="task-4-configure-the-construct-message-shape"></a>工作 4： 設定建構訊息圖形
「建構訊息」會保存訊息指派，包含 Begin、Edit 和 End Doc 程式碼的指示。  
  
 請使用下列程序設定「建構訊息」圖形。  
  
### <a name="to-configure-the-construct-message-shape"></a>若要設定建構訊息圖形  
  
1.  在 ReceiveBeginDoc 和 SendBeginDoc 之間拖放「建構訊息」圖形。  
  
    -   **建構的訊息：** BeginDocSessionMsg  
  
    -   **名稱：** ConstructBeginDocMessageWithSession  
  
    1.  將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。  
  
    2.  按兩下內圈的 MessageAssignment_1 圖形。  
  
         [BizTalk 運算式編輯器] 便會出現。  
  
    3.  輸入您的程式碼，例如：  
  
        ```  
        BeginDocSessionMsg = BeginDocMsg;  
        BeginDocSessionMsg(JDE.ReserveSession) = true;  
        BeginDocSessionMsg(JDE.SessionID) = 0;  
        ```  
  
         這會通知配接器您想要啟動工作階段。 SessionID 初始化為 0，但回應傳回時，J.D. Edwards EnterpriseOne 伺服器就會指派識別碼。  
  
     ![訊息運算式編輯器](../core/media/message-expression-editor.gif "message_expression_editor")  
  
2.  在 SendEditLine 之前拖曳「建構訊息」。  
  
    -   **建構的訊息：** EditLineSessionMsg  
  
    -   **名稱：** ConstructEditLineMessageWithSession  
  
     ![傳送編輯列](../core/media/constructoreditlinemessagewithsession.gif "constructoreditlinemessagewithsession")  
  
    1.  將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。  
  
    2.  按兩下內圈的 MessageAssignment_1 圖形。  
  
         [BizTalk 運算式編輯器] 便會出現。  
  
    3.  輸入您的程式碼，例如：  
  
        ```  
        EditLineSessionMsg = EditLineMsg;  
        EditLineSessionMsg(JDE.ReserveSession) = true;  
        EditLineSessionMsg(JDE.SessionID) =  
        BeginDocResponseMsg(JDE.SessionID);  
        ```  
  
     ![行編輯器編輯](../core/media/editline-editor.gif "editline_editor")  
  
3.  在 SendEndDoc 之前拖曳「建構訊息」圖形。  
  
    -   **建構的訊息：** EndDocSessionMsg  
  
    -   **名稱：** ConstructEndDocMessageWithSession  
  
    1.  將「訊息指派」圖形拖放到您要在其中建立新訊息的協調流程。  
  
    2.  按兩下內圈的 MessageAssignment_1 圖形。  
  
         [BizTalk 運算式編輯器] 便會出現。  
  
    3.  輸入您的程式碼，例如：  
  
        ```  
        EndDocSessionMsg = EndDocMsg;  
        EndDocSessionMsg(JDE.ReserveSession) = false;  
        EndDocSessionMsg(JDE.SessionID) =  
           BeginDocResponseMsg(JDE.SessionID);  
        ```  
  
## <a name="see-also"></a>另請參閱  
 [工作 1： 建立連接埠](../core/task-1-create-the-ports1.md)   
 [工作 2： 建立訊息](../core/task-2-create-the-messages2.md)   
 [工作 3： 設定傳送埠和接收圖形](../core/task-3-configure-the-send-and-receive-shapes2.md)   
 [工作 5： 設定轉換圖形](../core/task-5-configure-the-transform-shape2.md)