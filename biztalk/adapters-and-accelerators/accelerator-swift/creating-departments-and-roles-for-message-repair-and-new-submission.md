---
title: "建立部門和角色 Message Repair 和 New Submission |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- departments, creating
- creating, roles
- roles, requirements
- roles, creating
- creating, departments
- certificates, messages
- messages, certificates
ms.assetid: 6337bd57-63c5-4d97-b558-ac27d5eb60d7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d033ab3910657373f6e48b1f6e6bed076f730b51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-departments-and-roles-for-message-repair-and-new-submission"></a>Message Repair 和 New Submission 建立部門和角色
Message Repair 和 New Submission 牽涉到下列四個不同的作業：  
  
-   驗證失敗的訊息的修復  
  
-   修復 （包括重設金鑰） 的驗證  
  
-   核准的修復  
  
-   建立的新訊息  
  
 若要執行這些作業，使用者必須假設與作業相關聯的角色。 角色也必須處理部門 （如下所述） 的一部分。 若要在工作流程執行階段之後提交訊息，使用者必須與使用者相關聯的有效憑證簽署訊息。  
  
## <a name="creating-departments-and-roles"></a>建立部門和角色  
 設定檔的 Web 用戶端文件，請參閱。  
  
## <a name="rules-of-role-use"></a>角色，請使用規則  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者、 角色和部門必須符合下列規則：  
  
-   已修復的訊息的完整工作流程是要修復，確認，然後核准訊息。 建立訊息的完整工作流程是要建立、 修復、 確認，然後核准訊息。 驗證及核准步驟是選擇性的。  
  
-   部門的工作流程必須以建立角色或修復角色開頭。 如果工作流程包括建立和修復步驟 （工作流程建立訊息），建立步驟必須之前立即修復步驟。  
  
-   建立訊息的工作流程必須包含只有一個具有的功能建立的角色。  
  
-   每個工作流程必須包含只有一個角色具備的修復功能。  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者可以與一個以上的角色產生關聯，但沒有單一使用者可以執行單一工作流程中的多個步驟。 例如，如果使用者 A 修復訊息和使用者 B 驗證訊息，然後使用者 A 和使用者 B 都不可以核准訊息。  
  
-   沒有任何檢查角色或功能的 RekeyVerify 核准相對於其他角色與 RekeyVerify 或核准之功能的順序。  
  
-   如果您已修復的訊息無法通過驗證一次，它會回到 MRSR 網站文件庫中的修復收件匣。 當發生這種情況時，不再適用的驗證和核准者角色 （根據誰已經在工作流程中執行的角色） 上先前的限制。 例如，如果使用者 A 的訊息，使用者 B 的修復拒絕訊息驗證，與使用者 A 修復訊息第二次，然後使用者 B 以外的使用者無法檢查訊息。 如果是這樣，使用者 B 無法核准訊息。 另一個例子是，如果使用者 A 建立的訊息，使用者 B 會拒絕訊息中的驗證，而且使用者 C 修復訊息，則使用者無法確認訊息。  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立訊息的使用者也可以修復該訊息，如果它驗證失敗。  
  
-   只有[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]部門與工作流程關聯的使用者可以執行工作流程中的步驟。 當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者送出訊息時，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]會驗證使用者，包含與訊息相關聯的部門中的角色 （透過使用者設定檔 （如果部門不是預設值） 設定檔的 web 用戶端中）。  
  
-   系統管理員可以授與單一[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者在部門內的多個角色。 單一使用者可以執行修復、 驗證、 核准或建立或任何子集角色，但受限於上述任何一個工作流程上限制。  
  
## <a name="certificates"></a>憑證  
 若要提交訊息，以在本機電腦上的修復、 驗證、 核准或建立之後,[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者必須登入他 / 她憑證的訊息。 如需有關建立憑證的詳細資訊，請參閱[安裝憑證](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md)。  
  
 若要能夠將修復、 驗證、 核准，或藉由存取 MRSR 網站從遠端用戶端電腦建立一則訊息，使用者必須在 憑證-目前使用者/個人/憑證存放區 （使用者不需要其用戶端電腦加入他或她的憑證是系統管理員若要這樣做）。 此外，系統管理員在伺服器上的必須將使用者的憑證 （以及任何其他使用者從他們的用戶端電腦存取伺服器） 的憑證 （本機電腦） 儲存在伺服器上的其他人員/憑證 /。  
  
 單一使用者可能會有數個配置的角色，並執行任何這些角色時，應該使用相同的憑證。