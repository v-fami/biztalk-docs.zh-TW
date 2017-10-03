---
title: "處理和一致的訊息集 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAA
- messages, reconciled sets
ms.assetid: 05cd0cf6-f0fd-4cbe-83c6-1ed5f2da8822
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fc9f35f9381f82df90acb92e9536bbd967901a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="handling-reconciled-message-sets"></a>處理調節訊息設定
當 SAA 傳回的回應[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]位於 MessageBox 中記錄的回應，而且符合回應或原始訊息的回應。 您可以實作自訂的應用程式的行為，使用這項資訊。 若要這樣做，請開發實作特定客戶的反應，來調解的訊息/回應設定的自訂處理常式。 您可以建立自訂的處理常式，執行下列作業：  
  
-   處理的訊息有相互關聯的 FRR MTS21_FIN_ACKNAK 負值通知訊息，這表示，SWIFT 未順利收到來自訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 這可以讓 repairer 修正訊息並重新將它傳送到 SAA 和 SWIFT 網路，在修復後將會希望能夠成功接收訊息。 如需此解決方案的詳細資訊，請參閱[FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md)。  
  
-   卸除具有唯一的檔名表示的關聯性在集合中的訊息檔案資料夾到協調流程所發行的訊息回應設定。 然後，您可以在這些訊息上執行商務邏輯。  
  
-   處理序逾時訊息。  
  
-   記錄訊息傳輸的結果，然後捨棄真正的訊息。