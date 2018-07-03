---
title: 建立 Message Repair 和 New Submission 的部門和角色 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
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
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21abbaa8b5e3b36dfb5ad9091afa0e05a6d807d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988879"
---
# <a name="creating-departments-and-roles-for-message-repair-and-new-submission"></a>建立 Message Repair 和 New Submission 的部門和角色
Message Repair 和 New Submission 牽涉到下列四個不同的作業：  
  
- 驗證失敗的訊息的修復  
  
- 修復 （包括重設金鑰） 的驗證  
  
- 核准的修復  
  
- 建立的新訊息  
  
  若要執行這些作業，使用者必須假設與作業相關聯的角色。 角色也必須處理部門 （如下所述） 的一部分。 若要在工作流程執行階段之後提交訊息，使用者必須登入訊息，與使用者相關聯的有效憑證。  
  
## <a name="creating-departments-and-roles"></a>建立部門和角色  
 設定檔的 Web 用戶端文件，請參閱。  
  
## <a name="rules-of-role-use"></a>角色使用的規則  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] 使用者、 角色和部門必須符合下列規則：  
  
- 已修復的訊息的完整工作流程，就是修復、 驗證，然後核准訊息。 建立訊息的完整工作流程，就是建立、 修復、 驗證，然後核准訊息。 驗證與核准步驟是選擇性的。  
  
- 部門的工作流程必須與 create role 或修復角色開始。 如果工作流程包括建立和修復步驟 （建立訊息的工作流程），建立步驟必須在前面立即修復步驟。  
  
- 建立訊息的工作流程必須包含只能有一個具有一項功能建立的角色。  
  
- 每個工作流程必須包含可修復的功能只能有一個角色。  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者可以與一個以上的角色相關聯，但沒有單一使用者可以執行單一工作流程中的多個步驟。 例如，如果使用者的修復訊息，使用者 B 確認訊息，然後使用者 A 和使用者 B 都不可以核准訊息。  
  
- 不會檢查角色或功能的 RekeyVerify 核准相對於其他角色與 RekeyVerify 或核准之功能的順序。  
  
- 如果您已經修復訊息一次的驗證失敗，它會進入回 MRSR 網站文件庫中的修復收件匣。 當發生這種情況時，先前的限制 （根據使用者已經在工作流程中執行角色而定） 的驗證與核准者角色不再適用。 比方說，如果使用者的修復訊息，使用者 B 會拒絕在驗證和使用者的修復訊息訊息第二次，然後使用者 B 以外的使用者無法驗證訊息。 如果是這樣，使用者 B 可以核准訊息。 另一個例子是，如果使用者 A 會建立一則訊息，使用者 B 會拒絕驗證訊息，而且 C 使用者修復狀態訊息，則使用者無法確認訊息。  
  
- [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]建立訊息的使用者也可以修復該訊息，如果它驗證失敗。  
  
- 只有[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]部門工作流程相關聯的使用者可以執行工作流程中的步驟。 當[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者送出訊息時，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]確認使用者具有角色中的訊息相關聯的部門 （透過使用者設定檔 （如果部門不是預設值） 在 設定檔 web 用戶端）。  
  
- 系統管理員可以提供單一[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者在部門內的多個角色。 單一使用者可以執行修復、 驗證、 核准或建立或任何子集這些角色，但受限於上述任何一個工作流程限制。  
  
## <a name="certificates"></a>憑證  
 若要提交您的本機電腦上的訊息修復、 驗證、 核准或建立之後,[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]使用者必須登入他或她的憑證的訊息。 如需建立憑證的詳細資訊，請參閱[安裝的憑證](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md)。  
  
 若要能夠修復、 驗證、 核准，或從遠端用戶端電腦存取 MRSR 網站來建立一則訊息，使用者必須在 憑證-目前使用者/個人/憑證存放區的用戶端電腦 （使用者沒有加入他或她的憑證是系統管理員，若要這樣做）。 此外，在伺服器上的系統管理員必須加入使用者的憑證 （以及任何其他使用者從他們的用戶端電腦存取伺服器） 的憑證 （本機電腦） / 其他人員/憑證儲存在伺服器上。  
  
 單一使用者可能有數個配置的角色，並執行任何這些角色時，應該使用相同的憑證。