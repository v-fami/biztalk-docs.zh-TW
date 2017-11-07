---
title: "教學課程： 使用 TIBCO EMS 訊息內容屬性 |Microsoft 文件"
description: "若要針對 BizTalk Server 使用 TIBCO Enterprise Message Service 訊息描述元欄位，在協調流程中的逐步指南"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e52593b-5001-4740-89fb-e003e12d8e69
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f17b45afb28a497c0443f788a44d05307103c547
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="tutorial-use-tibco-ems-message-descriptors"></a>教學課程： 使用 TIBCO EMS 訊息描述元

## <a name="overview"></a>概觀
本教學課程將示範如何使用 BizTalk Server 內容屬性，以設定協調流程中的 TIBCO Enterprise Message Service (EMS) 訊息描述元欄位。 本教學課程是假設您的協調流程可以接收來自接收埠的訊息，而且可將訊息送至已繫結到 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 的傳送埠。  
  
 下列程序將示範如何透過變更 TibcoEMS.Priority 內容屬性的值，變更 TIBCO EMS 訊息的優先順序。 在 BizTalk Server 中，訊息都是永遠不變的。 因此，若要變更屬性值，您必須建立新訊息並加以修改。 在接收和傳送圖形之間插入訊息指派圖形，就可以建立新訊息和加以修改。 但首先您必須先參考結構描述 DLL，才能取得 TIBCO EMS 屬性的存取權。  
  
## <a name="reference-the-schema-dll"></a>參考結構描述 DLL  
  
1.  在 Visual Studio 中，開啟您的 BizTalk Server 專案，並開啟**方案總管 中**。  
  
2.  以滑鼠右鍵按一下**參考**，然後選取**加入參考**。  
  
     [新增參考] 對話方塊隨即出現。  
  
3.  按一下**瀏覽** 索引標籤。  
  
     **選取元件** 對話方塊隨即出現。  
  
4.  找出 **\<TIBCO EMS_Adapter_installation_directory > \bin**，然後選取**Microsoft.Adapters.TibcoEMSProperties.dll**。  
  
5.  按一下 **[開啟]**。  
  
     DLL 會出現在**選取的元件**中**加入參考** 對話方塊。  
  
6.  按一下**確定**，然後按兩下您的協調流程存取協調流程設計工具。  
  
7.  在**檢視**功能表上，指向**其他視窗**，然後按一下 **協調流程檢視**。  
  
8.  在協調流程檢視中，以滑鼠右鍵按一下**訊息**選取**新訊息**。  
  
9. 編輯新訊息的屬性，並指派**訊息類型**。  
  
     您要指派 Message_1 到 Message_2。 因此，這兩個訊息都必須指派相同的訊息類型。  
  
10. 在 [檢視] 功能表上，按一下 [工具箱]。  
  
11. 拖曳**訊息指派**圖形拖曳到您要建立新的訊息的協調流程。  
  
12. 編輯外圈的 ConstructMessage_1 圖形中，並選取您新的訊息，Message_2，**建構的訊息**屬性。  
  
13. 按兩下內圈的 MessageAssignment_1 圖形。  
  
     [BizTalk 運算式編輯器] 便會出現。  
  
14. 在 [BizTalk 運算式編輯器] 中，輸入您的程式碼。  
  
15. 一開始先貼上現有的訊息，然後為訊息內容屬性指定值。  
  
     語法是 `Message(property) = value;`。 例如：  
  
    ```  
    Message_2 = Message_1;  
    Message_2( TibcoEMS.Priority) = 6;  
    ```  
  
     如需取得可用於自訂訊息之支援屬性的清單，請參閱 TIBCO EMS。  
  
16. 按一下**確定**以關閉 BizTalk 運算式編輯器並儲存您的程式碼。  
  
17. 按一下 [傳送] 圖形，並指派**訊息**是**Message_2**。  
  
18. 確認訊息流程中的其餘圖形有在適當訊息上進行操作。  
  
19. 以滑鼠右鍵按一下方案總管 中的專案，然後選取**建置**。  
  
20. 以滑鼠右鍵按一下您的專案，然後選取**部署**。  
  
21. 選取**繫結**，**登錄**，和**啟動**測試您的協調流程 [BizTalk 總管] 中。  
  
## <a name="see-also"></a>另請參閱  
[TIBCO EMS 訊息內容屬性](../core/message-context-properties-in-biztalk-server.md)