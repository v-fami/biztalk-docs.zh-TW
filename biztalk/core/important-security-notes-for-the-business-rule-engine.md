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
ms.openlocfilehash: 9a90090c55dcbb0f8e55296d2711d5e4b36cd346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="important-security-notes-for-the-business-rule-engine"></a><span data-ttu-id="de27c-102">商務規則引擎的重要安全性注意事項</span><span class="sxs-lookup"><span data-stu-id="de27c-102">Important Security Notes for the Business Rule Engine</span></span>
<span data-ttu-id="de27c-103">本主題摘要說明 Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 中已知的安全性問題，以及降低安全性風險所需採取的步驟。</span><span class="sxs-lookup"><span data-stu-id="de27c-103">This topic summarizes known security issues in Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] and the steps you must take to mitigate the security risks.</span></span>  
  
## <a name="malicious-schema-input-causing-denial-of-service-attack"></a><span data-ttu-id="de27c-104">導致拒絕服務攻擊的惡意結構描述輸入</span><span class="sxs-lookup"><span data-stu-id="de27c-104">Malicious schema input causing Denial of Service attack</span></span>  
 <span data-ttu-id="de27c-105">在判斷提示事實時，各個規則均以符合原則中支援類型的所有物件加以驗證。</span><span class="sxs-lookup"><span data-stu-id="de27c-105">While asserting facts, each rule is verified against every object that matches the supported types within a policy.</span></span> <span data-ttu-id="de27c-106">假設原則中的一個規則使用利用選取器傳遞的結構描述中的一個項目。</span><span class="sxs-lookup"><span data-stu-id="de27c-106">Suppose there is a rule in a policy that uses one of the elements in a schema passed by using a selector.</span></span> <span data-ttu-id="de27c-107">現在，若符合選取器的此項目/屬性之執行個體重複數千次，且判斷提示每一個執行個體，則會導致效能降低，進而可能導致「拒絕服務」(DoS)。</span><span class="sxs-lookup"><span data-stu-id="de27c-107">Now if the instance if this element/attribute that matches the selector is repeated thousands of times, every such instance is asserted, causing performance degradation and subsequent possible Denial of Service (DoS).</span></span>  
  
 <span data-ttu-id="de27c-108">若要減輕此潛在問題，您必須驗證在執行原則時傳遞的所有模稜兩可的輸入。</span><span class="sxs-lookup"><span data-stu-id="de27c-108">To mitigate this potential issue, you need to validate all ambiguous input that is passed while executing a policy.</span></span>  
  
## <a name="ruleset-not-validating-objects-before-asserting-the-facts"></a><span data-ttu-id="de27c-109">規則集在判斷提示事實之前不驗證物件</span><span class="sxs-lookup"><span data-stu-id="de27c-109">RuleSet not validating objects before asserting the facts</span></span>  
 <span data-ttu-id="de27c-110">任何結構描述執行個體當做事實**RuleSet**不會針對結構描述驗證判斷提示規則使用選取器之前。</span><span class="sxs-lookup"><span data-stu-id="de27c-110">Any schema instance passed as a fact to the **RuleSet** is not validated against the schema before asserting any rules using selectors.</span></span> <span data-ttu-id="de27c-111">您應該要驗證執行原則時傳遞的所有輸入。</span><span class="sxs-lookup"><span data-stu-id="de27c-111">You should validate all input that is passed while executing a policy.</span></span>  
  
## <a name="expected-behaviors-of-the-business-rule-composer-when-rulestore-security-is-on"></a><span data-ttu-id="de27c-112">當 RuleStore 安全性開啟時商務規則編輯器的預期行為</span><span class="sxs-lookup"><span data-stu-id="de27c-112">Expected behaviors of the Business Rule Composer when RuleStore security is on</span></span>  
 <span data-ttu-id="de27c-113">您可以啟用規則存放區的角色為基礎的安全性功能，藉由呼叫**[rulestore]**方法**RuleStore**類別。</span><span class="sxs-lookup"><span data-stu-id="de27c-113">You can enable the role-based security feature for the rule store by calling the **EnableAuthorization** method of the **RuleStore** class.</span></span> <span data-ttu-id="de27c-114">當啟用此安全性功能時，「商務規則編輯器」的預期行為如下：</span><span class="sxs-lookup"><span data-stu-id="de27c-114">When this security feature is enabled, the expected behaviors in the Business Rule Composer are as follows:</span></span>  
  
-   <span data-ttu-id="de27c-115">物件模型會篩除使用者沒有讀取權限的規則集和詞彙。</span><span class="sxs-lookup"><span data-stu-id="de27c-115">The object model filters out rule sets and vocabularies to which the user does not have read access.</span></span> <span data-ttu-id="de27c-116">因此，它們不會出現在「商務規則編輯器」中。</span><span class="sxs-lookup"><span data-stu-id="de27c-116">Therefore, they do not appear in the Business Rule Composer.</span></span>  
  
-   <span data-ttu-id="de27c-117">若使用者沒有原則或詞彙的寫入權限，則嘗試儲存會造成擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="de27c-117">If the user does not have write access to a policy or a vocabulary, any save attempt causes an exception to be thrown.</span></span>  
  
## <a name="user-types-for-rule-store-administrator"></a><span data-ttu-id="de27c-118">規則存放區管理員的使用者類型</span><span class="sxs-lookup"><span data-stu-id="de27c-118">User types for rule store administrator</span></span>  
 <span data-ttu-id="de27c-119">規則存放區管理員擁有為儲存在規則存放區中的成品定義授權群組的權限。</span><span class="sxs-lookup"><span data-stu-id="de27c-119">The rule store administrator has the privilege to define an authorization group for artifacts saved in the rule store.</span></span> <span data-ttu-id="de27c-120">但是，請注意規則存放區管理員可能所屬的兩種使用者類型之間的以下差異：</span><span class="sxs-lookup"><span data-stu-id="de27c-120">However, note the following differences between two types of user to which the rule store administrator can belong:</span></span>  
  
-   <span data-ttu-id="de27c-121">當規則存放區管理員為 Windows 使用者時 (表示使用 Windows 驗證連接到規則存放區)，規則存放區管理員可定義使用者為 Windows 群組或 Windows 使用者的授權群組。</span><span class="sxs-lookup"><span data-stu-id="de27c-121">When the rule store administrator is a Windows user, which means using Windows authentication to connect the rule store, the rule store administrator can define an authorization group whose user is a Windows group or a Windows user.</span></span>  
  
-   <span data-ttu-id="de27c-122">當規則存放區管理員為 SQL 使用者時 (表示使用 SQL 驗證連接到規則存放區)，規則存放區管理員不能定義使用者為 Windows 群組的授權群組，但是可以定義使用者為 Windows 使用者的授權群組。</span><span class="sxs-lookup"><span data-stu-id="de27c-122">When the rule store administrator is a SQL user, which means using SQL authentication to connect the rule store, the rule store administrator cannot define an authorization group whose user is a Windows group, but can define an authorization group whose user is a Windows user.</span></span>  
  
## <a name="user-cannot-associate-an-authorization-group-with-an-artifact-without-sufficient-rights"></a><span data-ttu-id="de27c-123">權限不足的使用者不能為授權群組與成品建立關聯</span><span class="sxs-lookup"><span data-stu-id="de27c-123">User cannot associate an authorization group with an artifact without sufficient rights</span></span>  
 <span data-ttu-id="de27c-124">若成品建立者不是 SQL dbo 使用者，也不是 RE_ADMIN_USERS 成員，且對成品沒有 MODIFY_DELETE 權限，則不能為新的授權群組與成品建立關聯。</span><span class="sxs-lookup"><span data-stu-id="de27c-124">An artifact creator that is neither a SQL dbo user nor a member of RE_ADMIN_USERS, and does not have MODIFY_DELETE permission to an artifact, cannot associate a new authorization group with the artifact.</span></span> <span data-ttu-id="de27c-125">此行為範例如以下實例：</span><span class="sxs-lookup"><span data-stu-id="de27c-125">The following scenario is an example of this behavior:</span></span>  
  
1.  <span data-ttu-id="de27c-126">規則集建立者不是 dbo、不在 RE_ADMIN_USERS 群組中，在規則集建立之後也不具有 MODIFY_DELETE 權限。</span><span class="sxs-lookup"><span data-stu-id="de27c-126">Rule set creator is not dbo, is not in the RE_ADMIN_USERS group, and does not have MODIFY_DELETE permission after the rule set is created.</span></span>  
  
2.  <span data-ttu-id="de27c-127">建立者建立規則集。</span><span class="sxs-lookup"><span data-stu-id="de27c-127">Creator creates a rule set.</span></span>  
  
3.  <span data-ttu-id="de27c-128">RE_ADMIN_USERS 群組的成員建立具有 MODIFY_DELETE 權限的授權 AG1 給 User2。</span><span class="sxs-lookup"><span data-stu-id="de27c-128">Member of the RE_ADMIN_USERS group creates authorization AG1 with MODIFY_DELETE permission to User2.</span></span>  
  
4.  <span data-ttu-id="de27c-129">建立者將 AG1 與規則集建立關聯。</span><span class="sxs-lookup"><span data-stu-id="de27c-129">Creator associates AG1 with the rule set.</span></span>  
  
5.  <span data-ttu-id="de27c-130">啟用規則存放區授權。</span><span class="sxs-lookup"><span data-stu-id="de27c-130">Enable the rule store authorization.</span></span>  
  
6.  <span data-ttu-id="de27c-131">RE_ADMIN_USERS 群組的成員建立具有 READ_EXECUTE 權限的授權 AG2 給 User2。</span><span class="sxs-lookup"><span data-stu-id="de27c-131">Member of the RE_ADMIN_USERS group creates authorization AG2 with READ_EXECUTE permission to User2.</span></span>  
  
7.  <span data-ttu-id="de27c-132">建立者將 AG2 與規則集建立關聯。</span><span class="sxs-lookup"><span data-stu-id="de27c-132">Creator associates AG2 with the rule set.</span></span> <span data-ttu-id="de27c-133">雖然建立者沒有足夠的權限可執行，但未出現錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="de27c-133">Although the creator does not have sufficient right to do so, no error message appears.</span></span>  
  
8.  <span data-ttu-id="de27c-134">User2 嘗試讀取規則集失敗。</span><span class="sxs-lookup"><span data-stu-id="de27c-134">Attempt to read the rule set by User2 fails.</span></span>