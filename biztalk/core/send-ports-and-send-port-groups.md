---
title: 傳送埠與傳送埠群組 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, states
- send port groups
- send port groups, states
- send ports, about send ports
- send ports
- send port groups, about send port groups
- states, send ports
ms.assetid: 274bdd27-9098-46a2-8762-8b57bbfc95b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e57e56d05cf3b1a98bba83d0df92d52f09c6eda5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271822"
---
# <a name="send-ports-and-send-port-groups"></a>傳送埠與傳送埠群組
A*傳送埠*是 Microsoft BizTalk Server 傳送訊息的位置，或從中 BizTalk Server 接收訊息。 它也提供 BizTalk Server 用來實作通訊動作的技術。 連接埠的名稱可指出唯一的位置。  
  
 只要訊息傳送至傳送埠，就會建立新的傳送埠服務執行個體。 這稱為服務執行個體，也就是傳送埠執行個體。  
  
> [!NOTE]
>  適當的傳遞傳送埠可以只有一個執行個體。  
  
 A*傳送埠群組*是 BizTalk Server 可以使用相同的訊息傳送至一個組態中的多個目的地的傳送埠的具名的集合。  
  
 BizTalk Server 可以直接將訊息從接收位置路由至傳送埠或傳送埠群組。 BizTalk Server 將路由到傳送埠群組的訊息傳送到該群組中的所有傳送埠。  
  
 屬於傳送埠群組成員的傳送埠以下列兩種方式處理訊息：  
  
-   做為傳送埠群組的成員  
  
-   如同 BizTalk Server 直接將訊息路由至傳送埠  
  
## <a name="send-port-and-send-port-group-states"></a>傳送埠與傳送埠群組狀態  
 BizTalk 管理主控台會以下列其中一種狀態來顯示傳送埠與傳送埠群組：  
  
-   **繫結**。 使用 BizTalk Server 管理主控台，系統管理員可以將傳送埠或傳送埠群組繫結至協調流程。 在 BizTalk Server 將訊息路由至此傳送埠或傳送埠群組之前，系統管理員必須登錄並啟動繫結的傳送埠或傳送埠群組。  
  
-   **啟動**。 此傳送埠或傳送埠群組的訂閱已存在或在作用中。 當傳送埠或傳送埠群組為已啟動狀態時，BizTalk Server 會將訊息傳遞至傳送埠或傳送埠群組，讓傳送埠或傳送埠群組處理這些訊息。 在您啟動傳送埠或傳送埠群組之前，系統管理員必須使用 BizTalk 管理主控台登錄繫結的傳送埠或傳送埠群組。  
  
-   **停止**。 傳送埠或傳送埠群組目前並未執行。 如果您已啟動傳送埠或傳送埠群組，然後將它停止，會在工作佇列中繼續處理。 BizTalk Server 將路由至已停止的傳送埠或傳送埠群組的所有新訊息都傳送至執行傳送處理常式之主控件的擱置佇列。  
  
 下表顯示每個狀態可用的動作及其結果。  
  
||繫結|Stopped|Started|  
|------|-----------|-------------|-------------|  
|**登錄**|Stopped|無法使用|無法使用|  
|**啟動**|Started|Started|無法使用|  
|**停止**|無法使用|無法使用|Stopped|  
|**取消登錄**|無法使用|繫結|繫結|  
  
 傳送埠與其所屬傳送埠群組的組合狀態可用於判斷傳送埠或傳送埠群組是否處理訊息。  
  
 下表描述傳送埠和傳送埠群組的可能狀態組合。  
  
|訊息已傳送|傳送埠群組的狀態|傳送埠的狀態|結果|  
|------------------|------------------------------|------------------------|-------------|  
|直接至傳送埠|任何狀態|Started|訊息已處理|  
|直接至傳送埠|任何狀態|Stopped|訊息已擱置|  
|透過傳送埠群組到傳送埠|Started|Started|訊息已處理|  
|透過傳送埠群組到傳送埠|任何狀態|Stopped|訊息已擱置|  
|透過傳送埠群組到傳送埠|Stopped|任何狀態|訊息已擱置|  
  
## <a name="see-also"></a>另請參閱  
 [成品](../core/artifacts.md)