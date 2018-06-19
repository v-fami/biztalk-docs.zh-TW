---
title: 如何測試 HTTP 節點 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- HTTP node, testing
- testing HTTP node
ms.assetid: f6881e8f-9f92-4312-bb5e-06bbfb9fe0bb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2790a4e3fa0ff1ed9a9b9b0c2018108c9cbb1282
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255526"
---
# <a name="how-to-test-the-http-node"></a>如何測試 HTTP 節點
請依照以下步驟來測試 HTTP 節點。  
  
### <a name="to-test-the-http-node"></a>若要測試 HTTP 節點  
  
1.  在 PeopleSoft Enterprise 中，瀏覽至**PeopleTools**， **Integration Broker**，**監視器**， **Monitor Message**。  
  
     ![](../core/media/psadapter-40-task-gatewaytestnode.gif "PSAdapter_40_Task_GatewayTestNode")  
  
2.  按一下**節點狀態** 索引標籤。  
  
3.  在**Message Node Name**欄位中，輸入`MSEXTERNAL`，然後按一下 **查閱**圖示。  
  
4.  在下**Message Node Name**，選取**MSEXTERNAL**。  
  
     一則訊息隨即出現，並表示 PeopleSoft 正在透過 HTTP 進行通訊。  
  
     ![](../core/media/psadapter-41-task-gatewaytestsuccess.gif "PSAdapter_41_Task_GatewayTestSuccess")  
  
     如果您沒有收到訊息，請確認下列事項：  
  
    1.  在接收埠與節點之間的 IP 位址和連接埠都相符。  
  
    2.  BizTalk Server 正在執行。  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft HTTP 主控件和連接埠](../core/creating-a-peoplesoft-http-host-and-port.md)