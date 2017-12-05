---
title: "重要安全性注意事項商務規則引擎 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, store administrator
- Business Rule Composer, security
- business rules, security
- Denial of Service attacks
ms.assetid: 8972127a-5569-4b32-bc09-e9265efe9514
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e54a532d33e4f84eb5f1ecea67f957d415344a7c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="important-security-notes-for-the-business-rule-engine"></a>商務規則引擎的重要安全性注意事項
本主題摘要說明 Microsoft BizTalk Server，以及降低安全性風險時，必須採取的步驟中的已知的安全性問題。  
  
## <a name="malicious-schema-input-causing-denial-of-service-attack"></a>導致拒絕服務攻擊的惡意結構描述輸入  
 在判斷提示事實時，各個規則均以符合原則中支援類型的所有物件加以驗證。 假設原則中的一個規則使用利用選取器傳遞的結構描述中的一個項目。 現在，若符合選取器的此項目/屬性之執行個體重複數千次，且判斷提示每一個執行個體，則會導致效能降低，進而可能導致「拒絕服務」(DoS)。  
  
 若要減輕此潛在問題，您必須驗證在執行原則時傳遞的所有模稜兩可的輸入。  
  
## <a name="ruleset-not-validating-objects-before-asserting-the-facts"></a>規則集在判斷提示事實之前不驗證物件  
 任何結構描述執行個體當做事實**RuleSet**不會針對結構描述驗證判斷提示規則使用選取器之前。 您應該要驗證執行原則時傳遞的所有輸入。  
  
## <a name="expected-behaviors-of-the-business-rule-composer-when-rulestore-security-is-on"></a>當 RuleStore 安全性開啟時商務規則編輯器的預期行為  
 您可以啟用規則存放區的角色為基礎的安全性功能，藉由呼叫**[rulestore]**方法**RuleStore**類別。 當啟用此安全性功能時，「商務規則編輯器」的預期行為如下：  
  
-   物件模型會篩除使用者沒有讀取權限的規則集和詞彙。 因此，它們不會出現在「商務規則編輯器」中。  
  
-   若使用者沒有原則或詞彙的寫入權限，則嘗試儲存會造成擲回例外狀況。  
  
## <a name="user-types-for-rule-store-administrator"></a>規則存放區管理員的使用者類型  
 規則存放區管理員擁有為儲存在規則存放區中的成品定義授權群組的權限。 但是，請注意規則存放區管理員可能所屬的兩種使用者類型之間的以下差異：  
  
-   當規則存放區管理員為 Windows 使用者時 (表示使用 Windows 驗證連接到規則存放區)，規則存放區管理員可定義使用者為 Windows 群組或 Windows 使用者的授權群組。  
  
-   當規則存放區管理員為 SQL 使用者時 (表示使用 SQL 驗證連接到規則存放區)，規則存放區管理員不能定義使用者為 Windows 群組的授權群組，但是可以定義使用者為 Windows 使用者的授權群組。  
  
## <a name="user-cannot-associate-an-authorization-group-with-an-artifact-without-sufficient-rights"></a>權限不足的使用者不能為授權群組與成品建立關聯  
 若成品建立者不是 SQL dbo 使用者，也不是 RE_ADMIN_USERS 成員，且對成品沒有 MODIFY_DELETE 權限，則不能為新的授權群組與成品建立關聯。 此行為範例如以下實例：  
  
1.  規則集建立者不是 dbo、不在 RE_ADMIN_USERS 群組中，在規則集建立之後也不具有 MODIFY_DELETE 權限。  
  
2.  建立者建立規則集。  
  
3.  RE_ADMIN_USERS 群組的成員建立具有 MODIFY_DELETE 權限的授權 AG1 給 User2。  
  
4.  建立者將 AG1 與規則集建立關聯。  
  
5.  啟用規則存放區授權。  
  
6.  RE_ADMIN_USERS 群組的成員建立具有 READ_EXECUTE 權限的授權 AG2 給 User2。  
  
7.  建立者將 AG2 與規則集建立關聯。 雖然建立者沒有足夠的權限可執行，但未出現錯誤訊息。  
  
8.  User2 嘗試讀取規則集失敗。