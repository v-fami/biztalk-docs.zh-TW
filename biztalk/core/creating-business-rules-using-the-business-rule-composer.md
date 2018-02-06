---
title: "建立使用商務規則編輯器 」 的規則 |Microsoft 文件"
ms.custom: 
ms.date: 02/01/2018
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0600a2b2-36a2-4496-8ba1-c5f6e2fa4760
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74a4ccb0a4cdb7592dabfeb4dae96530c04cea38
ms.sourcegitcommit: 78376935362715684b451eb6da9f2b1e8c129c2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="create-business-rules-using-the-business-rule-composer"></a><span data-ttu-id="3010f-102">建立使用商務規則編輯器 」 的商務規則</span><span class="sxs-lookup"><span data-stu-id="3010f-102">Create Business Rules Using the Business Rule Composer</span></span>

## <a name="overview"></a><span data-ttu-id="3010f-103">概觀</span><span class="sxs-lookup"><span data-stu-id="3010f-103">Overview</span></span>
<span data-ttu-id="3010f-104">비즈니스 규칙 작성기를 사용하면 하나 이상의 비즈니스 규칙으로 비즈니스 정책을 만들 수 있으며 이러한 정책을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3010f-104">The Business Rule Composer allows you to create business policies with one or more business rules, and it allows you to deploy these policies.</span></span> <span data-ttu-id="3010f-105">또한 팩트(XML, 데이터베이스 및 .NET)를 찾아보고 비즈니스 규칙에서 팩트를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3010f-105">It also allows you to browse for facts (XML, database, and .NET), and use the facts in business rules.</span></span> <span data-ttu-id="3010f-106">뿐만 아니라 팩트를 기반으로 비즈니스 어휘를 만들고 비즈니스 규칙에서 이러한 어휘를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3010f-106">In addition, it allows you to create business vocabularies based on facts, and to use the vocabularies in business rules.</span></span>  
  
 <span data-ttu-id="3010f-107">이 섹션에서는 비즈니스 규칙 작성기를 사용하여 비즈니스 규칙을 만드는 작업 관련 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3010f-107">This section provides task-specific information about using the Business Rule Composer to create business rules.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="3010f-108">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="3010f-108">Next steps</span></span>
  
-   [<span data-ttu-id="3010f-109">啟動商務規則編輯器並載入原則</span><span class="sxs-lookup"><span data-stu-id="3010f-109">Start the Business Rule Composer and Load a Policy</span></span>](../core/how-to-start-the-business-rule-composer-and-load-a-policy.md)  
  
-   [<span data-ttu-id="3010f-110">商務規則編輯器的視窗</span><span class="sxs-lookup"><span data-stu-id="3010f-110">Windows of the Business Rule Composer</span></span>](../core/windows-of-the-business-rule-composer.md)  
  
-   [<span data-ttu-id="3010f-111">選取事實</span><span class="sxs-lookup"><span data-stu-id="3010f-111">Selecting Facts</span></span>](../core/selecting-facts.md)  
  
-   [<span data-ttu-id="3010f-112">建立原則和規則</span><span class="sxs-lookup"><span data-stu-id="3010f-112">Create Policies and Rules</span></span>](../core/how-to-create-policies-and-rules.md)  
  
-   [<span data-ttu-id="3010f-113">修改規則</span><span class="sxs-lookup"><span data-stu-id="3010f-113">Modify Rules</span></span>](../core/how-to-modify-rules.md)  
  
-   [<span data-ttu-id="3010f-114">維護原則版本</span><span class="sxs-lookup"><span data-stu-id="3010f-114">Maintain Policy Versions</span></span>](../core/how-to-maintain-policy-versions.md)  
  
-   [<span data-ttu-id="3010f-115">設定原則的事實擷取器</span><span class="sxs-lookup"><span data-stu-id="3010f-115">Configure a Fact Retriever for a Policy</span></span>](../core/how-to-configure-a-fact-retriever-for-a-policy.md)  
  
-   [<span data-ttu-id="3010f-116">開發詞彙</span><span class="sxs-lookup"><span data-stu-id="3010f-116">Develop Vocabularies</span></span>](../core/how-to-develop-vocabularies.md)  
  
-   [<span data-ttu-id="3010f-117">處理 Null 和 DBNull</span><span class="sxs-lookup"><span data-stu-id="3010f-117">Handle Null and DBNull</span></span>](../core/how-to-handle-null-and-dbnull.md)  
  
-   [<span data-ttu-id="3010f-118">分析商務規則中相同類型的多個物件</span><span class="sxs-lookup"><span data-stu-id="3010f-118">Analyze Multiple Objects of the Same Type in a Business Rule</span></span>](../core/how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule.md)  
  
-   [<span data-ttu-id="3010f-119">測試原則</span><span class="sxs-lookup"><span data-stu-id="3010f-119">Testing Policies</span></span>](../core/testing-policies.md)  
  
-   [<span data-ttu-id="3010f-120">eploy 和解除部署原則和詞彙</span><span class="sxs-lookup"><span data-stu-id="3010f-120">eploy and Undeploy Policies and Vocabularies</span></span>](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)  
  
-   [<span data-ttu-id="3010f-121">算術運算子</span><span class="sxs-lookup"><span data-stu-id="3010f-121">Arithmetic Operators</span></span>](../core/arithmetic-operators.md)  
  
-   [<span data-ttu-id="3010f-122">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="3010f-122">Logical Operators</span></span>](../core/logical-operators.md)  
  
-   [<span data-ttu-id="3010f-123">叫用原則，以從另一個原則</span><span class="sxs-lookup"><span data-stu-id="3010f-123">Invoke a Policy from Another Policy</span></span>](../core/invoking-a-policy-from-another-policy.md)  
  
-   [<span data-ttu-id="3010f-124">從原則傳回 True 或 False</span><span class="sxs-lookup"><span data-stu-id="3010f-124">Return True or False from a Policy</span></span>](../core/how-to-return-true-or-false-from-a-policy.md)
