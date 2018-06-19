---
title: 例外狀況的原因 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, errors
- errors, orchestrations
- errors, causes
ms.assetid: b0422382-d034-4c58-87c6-fc269dbbfe43
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9006234d71751078269e5a88559839fdadd91e91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232462"
---
# <a name="causes-of-exceptions"></a>造成例外狀況的原因
可透過下列方式在協調流程中產生例外狀況：  
  
-   由**擲回的例外狀況**圖形，立即且無條件地擲回例外狀況。 控制權會傳遞從**擲回的例外狀況**圖形直接以適當的例外狀況處理常式。  
  
-   透過在長時間執行之交易中過期的逾時。 預先定義的系統例外狀況：**Microsoft.XLANG.BaseTypes.TimeOutException**— 在此情況下會擲回。  
  
-   透過某個其他的交易失敗。 執行階段引擎會針對這些失敗擲回系統定義的訊息，例如 Microsoft.XLANG.BaseTypes.PersistenceException。  
  
-   透過使用者程式碼例外狀況。 在協調流程內進行外部使用者程式碼的呼叫時，所呼叫的 Common Language Runtime 類別可擲回例外狀況。 如果使用者程式碼中未處理這些例外狀況，這些例外狀況最後會往上傳播到呼叫使用者程式碼的範圍。  
  
-   透過某個其他系統例外狀況 (例如，持續性失敗、類似型別載入器例外狀況的另一個 .NET 或系統例外狀況，或是資料轉換錯誤)。  
  
> [!NOTE]
>  擲回型別載入器例外狀況時，可能不在攔截例外狀況**Catch 例外狀況**封鎖在相同**範圍**圖形。 這是因為此例外狀況是來自於型別載入器，而不是來自於 BizTalk 協調流程處理。 因此，它不會遵循 BizTalk 控制流程規則。  
  
-   根據周圍範圍終止執行中的同層級分支。 在此情況下，會將 Microsoft.XLANG.BaseTypes.ForcedTerminationException 擲回給每一個分支，而且您可能會想要對每一個分支加入例外狀況處理常式。 這類例外狀況處理常式無法重新擲回其例外狀況，也不應該嘗試擲回任何其他類型的例外狀況。  
  
-   透過接收指示錯誤的外部訊息。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤訊息](../core/fault-messages.md)   
 [例外狀況](../core/exceptions.md)