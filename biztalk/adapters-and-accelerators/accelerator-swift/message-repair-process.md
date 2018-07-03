---
title: 訊息修復程序 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- repairing messages
- errors, messages
- messages, errors
- validating, messages
- messages, validating
ms.assetid: 87b97cec-5796-4684-bcf0-53285aca7ee2
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb8e8cd5a23cd0187b5476688a00d1ca800c45d4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999063"
---
# <a name="message-repair-process"></a>Message Repair 程序
根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]會擱置失敗的訊息擱置佇列中的 MessageBox 資料庫。 此程序會處理失敗的訊息，分別從成功的訊息。 使用此預設的機制，不過，您有擷取失敗的訊息，並加以修復的能力有限。 訊息修復和 New Submission 功能[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]可讓[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]修復訊息並重新提交的使用者。 另一個[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者接著可以確認此修復狀態，以及第三個可以核准此修復狀態。  
  
> [!NOTE]
>  在此情況下，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者是部門的修復工作流程中執行角色的使用者。 此 A4SWIFT 使用者已定義，而且相關聯的憑證，在 設定檔 Web 用戶端的 使用者 連結。 這[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者不是相同[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者帳戶，如中所定義[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]群組中的使用者[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]電腦管理公用程式。 做為個人[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者必須擁有[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]使用者帳戶，以便提交訊息時，他們可以使用該帳戶的憑證。 不過，該人員也可以做為其他[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者： repairer、 驗證器、 核准者或建立者。 如需詳細資訊，請參閱 <<c0> [ 建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。  
  
 使用此修復工作流程，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]不會擱置失敗的訊息。 它在失敗的訊息中，執行額外的處理，然後將訊息置放在 MessageBox 中，就如同成功的訊息。 修復協調流程會將郵件分成[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]MRSR 站台，使用者可以執行其函式[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單。  
  
## <a name="message-validation"></a>訊息驗證  
 Message Repair 和 New Submission 會傳送任何訊息失敗修復 MRSR 網站的下列驗證：  
  
- 一般檔案剖析器 （未剖析的訊息） 所執行的結構化驗證  
  
- XML 驗證讀取器所執行的資料驗證  
  
- 執行商務規則引擎 (BRE) 的 SWIFT 網路和使用方式規則驗證  
  
  [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 收集 SWIFT 的訊息會跟著錯誤集合物件中的驗證期間遇到任何錯誤。 修復程序包含序列化成 XML，並將它附加到訊息格式錯誤的組件資訊時發生錯誤。 這項處理，也包含標示此升級的屬性，指出訊息已驗證失敗的訊息 ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed = = True)，並報告錯誤的另一個升級的屬性計算每個驗證階段。 產生的多部分訊息是由下列項目所組成：  
  
- 包含失敗的訊息內文部分  
  
- 包含錯誤集合的 XML 錯誤組件  
  
- 升級屬性指出失敗的狀態  
  
## <a name="message-repair"></a>Message Repair  
 內 MRSRDepartmentPolicy MRSRDepartmentRule 商務規則會判斷哪些部門將處理失敗的訊息。 訊息修復協調流程會開始修復工作流程會將訊息路由至收件匣中的部門修復角色相關聯。 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]執行修復角色的使用者開啟中的訊息[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]表單中，修復該郵件，然後簽署並將它提交。 協調流程會將修復的訊息傳送給每個修復、 重設金鑰驗證或核准的角色和工作流程已成功完成之後，會將訊息路由至傳送埠。  
  
 除了驗證，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]檢查以判斷下列訊息上的簽章：  
  
- 修復工作流程中的使用者屬於相同部門  
  
- 每位使用者已簽署一次  
  
- 對應至使用者角色的順序符合針對該部門所定義的工作流程中的順序  
  
  多個部門的詳細資訊，請參閱[建立部門和角色 Message Repair 和 New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)。  
  
  [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 也可讓您修復未剖析的訊息。 不過，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]修復未剖析的訊息上執行不同的處理。 如需詳細資訊，請參閱 <<c0> [ 修復未剖析的訊息](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)。