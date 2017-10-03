---
title: "如何建立新的 Gateway 節點 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: gateway nodes, creating
ms.assetid: e7c5f9a7-a58e-4661-9cb5-2414e31a57a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b371243d58389415349d5a88c05b7bf312e70ef9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-a-new-gateway-node"></a>如何建立新的 Gateway 節點
請遵循以下步驟，在 PeopleSoft Enterprise 中建立及設定新的 Gateway 節點。  
  
### <a name="to-create-and-configure-a-new-gateway-node"></a>若要建立和設定新的閘道節點  
  
1.  在 PeopleSoft 中，在左窗格中，按一下**節點定義**連結。  
  
2.  按一下**新增值** 索引標籤。  
  
3.  在**節點名稱**欄位中，輸入`MSEXTERNAL`，然後按一下 **新增**。  
  
4.  按一下**節點**索引標籤，然後輸入下列資訊：  
  
    1.  **描述：**輸入節點的描述。  
  
    2.  **節點型別：**選取**外部**。  
  
    3.  **路由類型：**選取**隱含**。  
  
     ![](../core/media/psadapter-34-task-gatewaynodeconnector.gif "PSAdapter_34_Task_GatewayNodeConnector")  
  
5.  按一下**連接器**索引標籤，然後輸入下列資訊：  
  
    1.  **閘道識別碼：**輸入`LOCAL`。  
  
    2.  **連接器識別碼：**輸入`HTTPTARGET`。  
  
     ![](../core/media/psadapter-35-task-gatewayhttptarget.gif "PSAdapter_35_Task_GatewayHTTPTarget")  
  
6.  按一下**查閱**圖示。  
  
7.  在下**連接器識別碼**，按一下  **HTTPTARGET**連結。  
  
     ![](../core/media/psadapter-36-task-gatewayconnectorid.gif "PSAdapter_36_Task_GatewayConnectorID")  
  
8.  在**屬性**索引標籤上，輸入下列資訊：  
  
    1.  **標頭：**輸入`Y`。  
  
    2.  **[Httpproperty]:**輸入`POST`。  
  
    3.  **[Primaryurl]:**輸入 IP 位址和連接埠的目標電腦 （開發電腦）。  
  
    > [!NOTE]
    >  **接收埠**先前設定。  
  
     ![](../core/media/psadapter-37-task-gatewaynodereceiveport.gif "PSAdapter_37_Task_GatewayNodeReceivePort")  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft HTTP 主控件和連接埠](../core/creating-a-peoplesoft-http-host-and-port.md)