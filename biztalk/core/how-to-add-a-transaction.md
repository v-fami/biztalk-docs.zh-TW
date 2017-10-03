---
title: "如何將異動加入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, transactions
- transactions, adding
ms.assetid: 25385c20-3025-4cf1-bc1f-ef266e081bad
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24c67a9c76ae87f2355bb0ea4638d3bd156cda6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-transaction"></a>如何新增交易
請依照下列步驟來新增交易。  
  
### <a name="to-add-a-transaction"></a>新增交易  
  
1.  按一下**交易** 索引標籤。  
  
2.  按一下**加入異動**。  
  
3.  按一下**新增值**。 輸入下列資訊，然後再按一下**新增**。  
  
    1.  **節點名稱：**確認這是**MSEXTERNAL**。  
  
    2.  **交易類型：**確認這是**Outbound Asynchronous**。  
  
    3.  **要求訊息：**輸入`LOCATION_SYNC`。  
  
    4.  **要求訊息版本：**輸入`VERSION_1`。  
  
     ![](../core/media/psadapter-38-task-gatewayaddtransaction.gif "PSAdapter_38_Task_GatewayAddTransaction")  
  
4.  在**交易詳細資料**索引標籤上，確認下列設定：  
  
    1.  **狀態：**作用中。  
  
    2.  **路由：**隱含。  
  
     ![](../core/media/psadapter-39-task-gatewaytransdetail.gif "PSAdapter_39_Task_GatewayTransDetail")  
  
5.  按一下 **[儲存]**。  
  
6.  按一下**回到交易清單**連結。  
  
     這筆交易會顯示在交易清單中。  
  
## <a name="see-also"></a>另請參閱  
 [建立 PeopleSoft HTTP 主控件和連接埠](../core/creating-a-peoplesoft-http-host-and-port.md)