---
title: 移除的使用方式規則驗證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- policies, deleting rules
- rules
ms.assetid: b2b0dabf-8f99-4b85-95da-6bbf3e79ad41
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 017184e5f530096dc0ca166fdaaa9810a3372cfa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962116"
---
# <a name="removing-usage-rule-validation"></a><span data-ttu-id="01b99-102">移除的使用方式規則驗證</span><span class="sxs-lookup"><span data-stu-id="01b99-102">Removing Usage Rule Validation</span></span>
<span data-ttu-id="01b99-103">使用規則 SWIFT 標準中定義且由強制執行[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]特定的每個訊息類型的商務原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-103">Usage rules are defined in SWIFT standards and enforced by [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] business policies specific to each message type.</span></span> <span data-ttu-id="01b99-104">這些使用規則是您可用來提供額外的驗證欄位的指導方針。</span><span class="sxs-lookup"><span data-stu-id="01b99-104">These usage rules are guidelines that you can use to provide extra validation for a field.</span></span> <span data-ttu-id="01b99-105">與不同的是網路驗證規則都是必要項，您可以選擇不使用規則所需的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="01b99-105">Unlike network validation rules, which are mandatory, you can choose not to require usage rules for a message type.</span></span> <span data-ttu-id="01b99-106">如果是這樣，您可以執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="01b99-106">If that is the case, you can do either of the following:</span></span>  
  
-   <span data-ttu-id="01b99-107">您可以移除特定的商務規則，以強制使用規則和訊息類型驗證原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-107">You can remove a specific business rule that enforces a usage rule from the message-type validation policy.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="01b99-108">從原則移除規則將它永久移除。</span><span class="sxs-lookup"><span data-stu-id="01b99-108">Removing a rule from the policy will remove it permanently.</span></span>  
  
-   <span data-ttu-id="01b99-109">如果您不要在任何使用規則強制執行，您可以解除部署的訊息類型的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-109">If you do not want to enforce any of the usage rules, you can undeploy the validation policy for a message type.</span></span>  
  
### <a name="to-remove-a-rule-from-a-policy"></a><span data-ttu-id="01b99-110">若要從原則移除規則</span><span class="sxs-lookup"><span data-stu-id="01b99-110">To remove a rule from a policy</span></span>  
  
1.  <span data-ttu-id="01b99-111">在文字編輯器中，例如 [記事本] 開啟您想要變更，例如，在 MT103_Validation_Policy 的驗證原則*\<磁碟機\>*: files\ Microsoft BizTalk Accelerator for SWIFT \<版本\>訊息 Pack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category 1\MT103。</span><span class="sxs-lookup"><span data-stu-id="01b99-111">In a text editor, such as Notepad, open the validation policy that you want to change, for example, MT103_Validation_Policy in *\<drive\>*:\Program Files\ Microsoft BizTalk Accelerator for SWIFT \<version\> Message Pack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category 1\MT103.</span></span>  
  
2.  <span data-ttu-id="01b99-112">移除規則 節點，不想，並再儲存原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-112">Remove the rule node that you do not want, and then save the policy.</span></span>  
  
3.  <span data-ttu-id="01b99-113">使用商務規則引擎部署精靈來發佈和部署原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-113">Use the Business Rules Engine Deployment Wizard to publish and deploy the policy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01b99-114">您也可以從 驗證原則移除規則，藉由建立一份原則中，移除特定規則，然後部署已修改的原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-114">You can also remove a rule from a validation policy by creating a copy of the policy, removing the specific rule, and then deploying the modified policy.</span></span> <span data-ttu-id="01b99-115">解除部署原則的舊版。</span><span class="sxs-lookup"><span data-stu-id="01b99-115">Undeploy the previous version of the policy.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="01b99-116">在商務規則編輯器 中，您無法刪除規則從已發行或部署的原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-116">In Business Rule Composer, you cannot delete a rule from a published or deployed policy.</span></span>  
  
### <a name="to-remove-the-policy-for-a-message-type"></a><span data-ttu-id="01b99-117">若要移除的訊息類型的原則</span><span class="sxs-lookup"><span data-stu-id="01b99-117">To remove the policy for a message type</span></span>  
  
1.  <span data-ttu-id="01b99-118">按一下**啟動**，指向 **程式**，指向  **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下 **商務規則編輯器 」**。</span><span class="sxs-lookup"><span data-stu-id="01b99-118">Click **Start**, point to **Programs**, point to **Microsoft**[!INCLUDE[btsBizTalkServer2006r3ui](../../includes/btsbiztalkserver2006r3ui-md.md)], and then click **Business Rule Composer**.</span></span>  
  
2.  <span data-ttu-id="01b99-119">在原則總管 中，找到的訊息類型，例如 MT103_Validation_Policy 已部署的驗證原則。</span><span class="sxs-lookup"><span data-stu-id="01b99-119">In Policy Explorer, find the deployed validation policy for the message type, for example, MT103_Validation_Policy.</span></span>  
  
3.  <span data-ttu-id="01b99-120">以滑鼠右鍵按一下原則，請按一下**解除部署**，按一下 **刪除**，然後按一下 **是**。</span><span class="sxs-lookup"><span data-stu-id="01b99-120">Right-click the policy, click **Undeploy**, click **Delete**, and then click **Yes**.</span></span>