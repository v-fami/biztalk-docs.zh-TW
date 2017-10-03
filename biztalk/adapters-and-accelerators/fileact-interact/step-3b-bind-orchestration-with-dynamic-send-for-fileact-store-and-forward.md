---
title: "步驟 3B: FileAct 存放與轉寄 （提取） 案例的動態傳送埠與協調流程繫結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb973066-8797-4f51-a89e-3845f2811605
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10111de1080aacd532be96f501be1d20acda1dc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-bind-the-orchestration-with-dynamic-send-port-for-fileact-store-and-forward-pull-scenario"></a>步驟 3B: FileAct 存放與轉寄 （提取） 案例的動態傳送埠與協調流程繫結
在開始此步驟之前，必須先完成[步驟 3A： 建立 FileAct 存放與轉寄 （提取） 案例的動態傳送埠的協調流程](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md)。  
  
### <a name="to-add-a-file-receive-location"></a>若要新增 FILE 接收位置  
  
1.  啟動**BizTalk Server 管理**。  
  
2.  在 BizTalk Server 管理主控台的左窗格中，展開 BizTalk Server 管理 中，展開**BizTalk 群組**，依序展開**平台設定**，然後按一下 **主控件執行個體**. 確認的狀態**BizTalkServerApplication**裝載執行個體和 FileActhost 是**執行**。 如果沒有，請以滑鼠右鍵按一下主控件執行個體，然後按一下**啟動**。  
  
3.  在左窗格中，展開 應用程式，然後再展開 BizTalk Application 1。 按一下 協調流程。  
  
4.  以滑鼠右鍵按一下**DynamicSendOrchestration**按一下**屬性**。  
  
5.  在**協調流程屬性**] 對話方塊的左窗格中，按一下 [**繫結**並執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**Host**|從下拉式清單選取**BizTalkServer 應用程式**。|  
    |**動態提取**|從下拉式清單選取**Tutorial_FA_DynamicSendPort**。|  
    |**SendPullResponseToSender**|從下拉式清單選取**Tutorial_FA_SendPullResponsetoReceiver**。|  
  
## <a name="see-also"></a>另請參閱  
 [步驟 3A： 建立 FileAct 存放與轉寄 （提取） 案例的動態傳送埠的協調流程](../../adapters-and-accelerators/fileact-interact/step-3a-create-orchestration-for-dynamic-send-port-fileact-store-and-forward.md)