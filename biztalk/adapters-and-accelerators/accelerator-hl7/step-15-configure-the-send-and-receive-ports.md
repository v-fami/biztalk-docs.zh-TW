---
title: "步驟 15： 設定傳送埠和接收埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message enrichment tutorial, ports
ms.assetid: d532b196-473e-4c8f-b4ed-acef674fc698
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 020d83db1db86f9ff9ce116578cf58f19ba08241
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-15-configure-the-send-and-receive-ports"></a>步驟 15： 設定傳送埠和接收埠
在上一個步驟中，您可以建立邏輯傳送和接收埠使用協調流程設計師並設定連接埠繫結到 「 稍後指定 」。 在此步驟中，您可以使用 BizTalk 總管 中定義實體的來源和目的地位置，並以您在協調流程中建立的邏輯連接埠繫結的實體連接埠完成連接埠設定。  
  
## <a name="configure-the-send-and-receive-ports"></a>設定傳送埠和接收埠  
  
1.  在 BizTalk Server 管理主控台中，依序展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，依序展開**應用程式**，然後展開  **BizTalk Application 1**。  
  
2.  以滑鼠右鍵按一下**傳送埠**，指向 [新增]，然後按一下**靜態單向傳送埠**。  
  
3.  在 [傳送埠屬性] 對話方塊中**名稱**方塊中，輸入**MLLPSendPort**。  
  
4.  如**類型**，選取**MLLP**。  
  
5.  按一下**設定**按鈕右邊的**類型**欄位。  
  
6.  在 [MLLP 傳輸屬性] 對話方塊的**連接名稱**輸入**MLLPConnection**。 如**主機**輸入**localhost**。 按一下 **[確定]**。  
  
7.  在傳送埠屬性 對話方塊中，如**傳送管線**，選取**BTAHL72XPipelines.BTAHL72XSendPipeline**，然後按一下**確定**。  
  
8.  在管理主控台中，以滑鼠右鍵按一下**MLLPSendPort**連接埠，，然後按一下 **啟動**。  
  
9. 展開**平台設定**，按一下 **主控件執行個體**，以滑鼠右鍵按一下**BizTalkServerApplication**，然後按一下 **啟動**。 如果主機已在執行中，按一下**重新啟動**。  
  
10. 按一下**協調流程**，以滑鼠右鍵按一下**BTAHL7_Project.Doorbell_Orchestration**，然後按一下 **屬性**。  
  
11. 在 [協調流程屬性] 對話方塊的主控台樹狀目錄中，按一下**繫結**。  
  
12. 在**繫結** 窗格中，針對**主機**，選取**BizTalkServerApplication**。  
  
13. 如**SOAPReceivePort**，選取**WebPort_BTAHL7_Project_Proxy/BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**中**接收埠**資料行。  
  
14. 如**MLLPSendPort**，選取**MLLPSendPort**中**傳送埠/傳送埠群組**資料行。  
  
15. 按一下**確定**儲存的變更。  
  
## <a name="msh-5-and-msh-6"></a>MSH 5 和 MSH 6  
 MSH 5 和 MSH 6 標頭欄位會分別包含的目的端應用程式和功能。 在組態總管 中，您可以 MSH 5 和 MSH 6 的情況下，當您想要變更訊息中的目的地資訊中的三個元件的每個指定的值。 這是這種情況，當原始的訊息不包含合作對象特有的資訊。 這個步驟是適用於宣告式 （發行者/訂閱者） 模型。 如果適用的話，您的環境中，您可以執行此步驟。 如需有關如何設定這些值的詳細資訊，請參閱[合作對象-BTAHL7 Configuration 總管](parties-tab.md)。  
  
 若要繼續[步驟 16： 啟動協調流程](../../adapters-and-accelerators/accelerator-hl7/step-16-start-the-orchestration.md)。  
  
## <a name="see-also"></a>另請參閱  
 [訊息擴充教學課程](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)