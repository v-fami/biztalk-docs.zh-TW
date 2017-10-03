---
title: "FRR NAK 處理常式範例的運作方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9f11bd20-3a0e-4d96-8e0a-32fecc7eed7e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 009cb0c3dffce5f88c72207866f6778e3deb7b28
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-frr-nak-handler-sample-works"></a>FRR NAK 處理常式範例的運作方式
範例 FRR NAK 自訂處理常式做為 FIN 回應對帳 (FRR) 協調流程與訊息修復協調流程之間的媒介。 FRR 協調流程中指出的 SWIFT 網路嘗試接收訊息時發生錯誤。 FRR 協調流程的輸出是一段訊息與錯誤物件。 FRR NAK 自訂處理常式會將該訊息轉換成的兩個部分訊息，指出錯誤發生時，啟用要由訊息修復協調流程收取訊息的錯誤組件。 開啟 訊息修復協調流程中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]可讓您找出錯誤的是，修復的訊息，因此，並重新送出的表單，讓[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]可以重新傳送至 SAA。  
  
 FRR NAK 自訂處理常式處理的 SWIFT 網路無法成功接收訊息時，就會執行下列步驟：  
  
1.  FRR 協調流程有相互關聯的 MTS21_FIN_ACKNAK NAK 訊息失敗的訊息之後，RepairSWIFTRejectedMessage 協調流程 （自訂的處理常式） 會拾取原始訊息 MessageBox。 它沒有，因為它會篩選 A4SWIFT_FRRFailed = = True 和 A4SWIFT_SendingServiceType ="A4SWIFT_FrrService"。  
  
2.  自訂處理常式不會拾取 MTS21_FIN_ACKNAK NAK 相關訊息，FRR 原始訊息。 相反地，它會建立錯誤集合物件、 填入 BRE 驗證錯誤，指出哪些 A4SWIFT_FRRFailedReason 屬性，然後將它加入至原始訊息。 訊息修復協調流程可以處理這兩個部分則訊息。  
  
3.  自訂處理常式會升級下列屬性會收取訊息修復協調流程的訊息： A4SWIFT_Failed = = True，A4SWIFT_SwiftBound = = True，而且 BTS。作業 ="A4SWIFT_DASMMarkedAsFailed"。 它會設定為 2，組件屬性的數目，並設定適當的錯誤屬性。  
  
4.  因為升級的屬性，而訊息修復協調流程才能收取訊息，而 RepairSWIFTRejectedMessage 協調流程會終止。