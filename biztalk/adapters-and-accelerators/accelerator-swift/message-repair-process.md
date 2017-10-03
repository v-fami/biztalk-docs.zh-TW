---
title: "訊息修復程序 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- errors, messages
- messages, errors
- validating, messages
- messages, validating
ms.assetid: 87b97cec-5796-4684-bcf0-53285aca7ee2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 442e49c347b4adf84dd7e6ee86c3b3595452cb34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-process"></a>訊息修復程序
根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會擱置失敗的訊息擱置佇列中的 MessageBox 資料庫。 此程序會處理失敗的訊息分開成功訊息。 使用此預設的機制，不過，您必須擷取失敗的訊息，並加以修復的能力有限。 訊息修復和 New Submission 功能[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]啟用[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]修復訊息，然後再重新送出的使用者。 另一個[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接著使用者可確認修復，以及第三個可以核准修復。  
  
> [!NOTE]
>  在此內容中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者是部門修復工作流程中執行角色的使用者。 此 A4SWIFT 使用者已定義，而且相關聯的憑證，在設定檔的 Web 用戶端的 [使用者] 連結。 這[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者不是相同[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者帳戶中所定義[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者群組中[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式。 做為人員[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者必須擁有[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者帳戶，使其可以傳送訊息時，使用該帳戶的憑證。 不過，該人員也可以當做其他[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者： repairer、 驗證、 核准者或建立者。 如需詳細資訊，請參閱[建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。  
  
 使用此修復工作流程，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會擱置失敗的訊息。 它對失敗的訊息，執行額外處理，並再將訊息置放在 MessageBox 中，便能夠成功的訊息。 修復協調流程會捨棄訊息到[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 站台，使用者可以執行其函式中的[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。  
  
## <a name="message-validation"></a>訊息驗證  
 Message Repair 和 New Submission 會傳送任何訊息至 MRSR 站台修復下列驗證失敗：  
  
-   一般檔案剖析器 （未剖析訊息） 所執行的結構化驗證  
  
-   XML 驗證讀取器所執行的資料驗證  
  
-   執行商務規則引擎 (BRE) 的 SWIFT 網路和使用方式規則驗證  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]收集 SWIFT 的訊息會跟著錯誤集合物件中驗證期間發生任何錯誤。 修復程序包含序列化為 XML，以及將它連接至做為部分錯誤訊息資訊時發生錯誤。 這項處理，也包含標記與升級屬性，指出訊息已驗證失敗的訊息 ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = True)，並報告錯誤的其他升級的屬性會計算每個驗證階段。 產生的多部分訊息是由下列項目所組成：  
  
-   包含失敗的訊息內文部分  
  
-   包含錯誤集合 XML 錯誤組件  
  
-   升級屬性指出失敗的狀態  
  
## <a name="message-repair"></a>訊息修復  
 MRSRDepartmentRule 商務規則內 MRSRDepartmentPolicy 決定哪個部門將處理失敗的訊息。 訊息修復協調流程會開始修復工作流程會將訊息路由至收件匣部門中的修復角色相關聯。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]執行修復角色的使用者開啟中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單中，修復訊息，然後簽署，並將它提交。 協調流程將修復的訊息路由傳送至每個修復、 重設金鑰驗證或核准角色和工作流程已順利完成之後，會將訊息路由至傳送埠。  
  
 驗證，除了[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會檢查訊息，以判斷下列上的簽章：  
  
-   修復工作流程中的使用者屬於相同的部門  
  
-   每個使用者登一次  
  
-   對應至使用者角色的順序符合針對該部門所定義的工作流程中的順序  
  
 如需部門的詳細資訊，請參閱[建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]也可讓您修復未剖析的訊息。 不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]修復未剖析訊息上執行不同的處理。 如需詳細資訊，請參閱[修復未剖析訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。