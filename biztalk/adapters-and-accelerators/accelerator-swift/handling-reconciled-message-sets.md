---
title: 處理和一致的訊息集 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAA
- messages, reconciled sets
ms.assetid: 05cd0cf6-f0fd-4cbe-83c6-1ed5f2da8822
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d3a06955e0072348098ddd7f191bf4862fb119a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986087"
---
# <a name="handling-reconciled-message-sets"></a>處理協調的訊息集
當 SAA 將回應傳回給[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]記錄位於 MessageBox 中的回應，並比對回應或原始訊息的回應。 您可以實作自訂的應用程式的行為，使用這項資訊。 若要這樣做，請開發實作特定客戶的反應和一致的訊息回應集的自訂處理常式。 您可以建立自訂的處理常式，執行下列作業：  

- 處理 MTS21_FIN_ACKNAK 負值通知訊息，這會指出 SWIFT 未成功接收來自訊息的 FRR 有相互關聯訊息[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。 這可以讓 repairer 修正訊息，並重新傳送給 SAA 和 SWIFT 網路，在修復後將會希望能夠成功接收訊息。 如需有關此解決方案的詳細資訊，請參閱[FRR NAK 處理常式範例](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md)。  

- 拖放入檔案資料夾中的協調流程發佈其唯一的檔案名稱表示的關聯性集合中的訊息的訊息回應設定。 然後，您就可以執行商務邏輯上這些訊息。  

- 處理逾時訊息。  

- 記錄訊息傳輸的結果，並捨棄實際的訊息。
