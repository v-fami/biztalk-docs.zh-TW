---
title: "使用商務規則編輯器建立商務規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, business rules
- business rules, creating
ms.assetid: 0600a2b2-36a2-4496-8ba1-c5f6e2fa4760
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b5b1281acab139159dd837f63cf80af56d388c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-business-rules-using-the-business-rule-composer"></a><span data-ttu-id="5372d-102">使用商務規則編輯器建立商務規則</span><span class="sxs-lookup"><span data-stu-id="5372d-102">Creating Business Rules Using the Business Rule Composer</span></span>
<span data-ttu-id="5372d-103">「商務規則編輯器」可讓您建立含有一或多項商務規則的商務原則，並可讓您部署這些原則。</span><span class="sxs-lookup"><span data-stu-id="5372d-103">The Business Rule Composer allows you to create business policies with one or more business rules, and it allows you to deploy these policies.</span></span> <span data-ttu-id="5372d-104">其也可讓您瀏覽事實 (XML、資料庫和 .NET)，並在商務規則中使用這些事實。</span><span class="sxs-lookup"><span data-stu-id="5372d-104">It also allows you to browse for facts (XML, database, and .NET), and use the facts in business rules.</span></span> <span data-ttu-id="5372d-105">此外，其還可讓您根據事實建立商務詞彙，並在商務規則中使用這些詞彙。</span><span class="sxs-lookup"><span data-stu-id="5372d-105">In addition, it allows you to create business vocabularies based on facts, and to use the vocabularies in business rules.</span></span>  
  
 <span data-ttu-id="5372d-106">本節提供有關使用「商務規則編輯器」以建立商務規則的工作特定資訊。</span><span class="sxs-lookup"><span data-stu-id="5372d-106">This section provides task-specific information about using the Business Rule Composer to create business rules.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5372d-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="5372d-107">In This Section</span></span>  
  
-   [<span data-ttu-id="5372d-108">如何啟動 「 商務規則編輯器 」 和載入原則</span><span class="sxs-lookup"><span data-stu-id="5372d-108">How to Start the Business Rule Composer and Load a Policy</span></span>](../core/how-to-start-the-business-rule-composer-and-load-a-policy.md)  
  
-   [<span data-ttu-id="5372d-109">商務規則編輯器的視窗</span><span class="sxs-lookup"><span data-stu-id="5372d-109">Windows of the Business Rule Composer</span></span>](../core/windows-of-the-business-rule-composer.md)  
  
-   [<span data-ttu-id="5372d-110">選取事實</span><span class="sxs-lookup"><span data-stu-id="5372d-110">Selecting Facts</span></span>](../core/selecting-facts.md)  
  
-   [<span data-ttu-id="5372d-111">如何建立原則和規則</span><span class="sxs-lookup"><span data-stu-id="5372d-111">How to Create Policies and Rules</span></span>](../core/how-to-create-policies-and-rules.md)  
  
-   [<span data-ttu-id="5372d-112">如何修改規則</span><span class="sxs-lookup"><span data-stu-id="5372d-112">How to Modify Rules</span></span>](../core/how-to-modify-rules.md)  
  
-   [<span data-ttu-id="5372d-113">如何維護原則版本</span><span class="sxs-lookup"><span data-stu-id="5372d-113">How to Maintain Policy Versions</span></span>](../core/how-to-maintain-policy-versions.md)  
  
-   [<span data-ttu-id="5372d-114">如何設定原則的事實擷取器</span><span class="sxs-lookup"><span data-stu-id="5372d-114">How to Configure a Fact Retriever for a Policy</span></span>](../core/how-to-configure-a-fact-retriever-for-a-policy.md)  
  
-   [<span data-ttu-id="5372d-115">如何開發詞彙</span><span class="sxs-lookup"><span data-stu-id="5372d-115">How to Develop Vocabularies</span></span>](../core/how-to-develop-vocabularies.md)  
  
-   [<span data-ttu-id="5372d-116">如何處理 Null 和 DBNull</span><span class="sxs-lookup"><span data-stu-id="5372d-116">How to Handle Null and DBNull</span></span>](../core/how-to-handle-null-and-dbnull.md)  
  
-   [<span data-ttu-id="5372d-117">如何分析商務規則中相同類型的多個物件</span><span class="sxs-lookup"><span data-stu-id="5372d-117">How to Analyze Multiple Objects of the Same Type in a Business Rule</span></span>](../core/how-to-analyze-multiple-objects-of-the-same-type-in-a-business-rule.md)  
  
-   [<span data-ttu-id="5372d-118">測試原則</span><span class="sxs-lookup"><span data-stu-id="5372d-118">Testing Policies</span></span>](../core/testing-policies.md)  
  
-   [<span data-ttu-id="5372d-119">如何部署和解除部署原則和詞彙</span><span class="sxs-lookup"><span data-stu-id="5372d-119">How to Deploy and Undeploy Policies and Vocabularies</span></span>](../core/how-to-deploy-and-undeploy-policies-and-vocabularies.md)  
  
-   [<span data-ttu-id="5372d-120">算術運算子</span><span class="sxs-lookup"><span data-stu-id="5372d-120">Arithmetic Operators</span></span>](../core/arithmetic-operators.md)  
  
-   [<span data-ttu-id="5372d-121">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="5372d-121">Logical Operators</span></span>](../core/logical-operators.md)  
  
-   [<span data-ttu-id="5372d-122">叫用原則，以從另一個原則</span><span class="sxs-lookup"><span data-stu-id="5372d-122">Invoking a Policy from Another Policy</span></span>](../core/invoking-a-policy-from-another-policy.md)  
  
-   [<span data-ttu-id="5372d-123">如何從原則傳回 True 或 False</span><span class="sxs-lookup"><span data-stu-id="5372d-123">How to Return True or False from a Policy</span></span>](../core/how-to-return-true-or-false-from-a-policy.md)