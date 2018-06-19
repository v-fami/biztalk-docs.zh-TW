---
title: 詞彙 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- business rules, vocabularies
- vocabularies, about vocabularies
- vocabularies
- Business Rules Engine, vocabularies
ms.assetid: 591673a0-2c4d-41ca-9997-b363c086dd66
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9e20dfead51d54822d3316c8819d04a259cfa83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288006"
---
# <a name="vocabularies"></a><span data-ttu-id="fdf15-102">詞彙</span><span class="sxs-lookup"><span data-stu-id="fdf15-102">Vocabularies</span></span>
<span data-ttu-id="fdf15-103">用以定義規則條件與動作的詞彙通常是以網域或業界特定的術語來表達。</span><span class="sxs-lookup"><span data-stu-id="fdf15-103">The terms used to define rule conditions and actions are usually expressed by domain or industry-specific nomenclature.</span></span> <span data-ttu-id="fdf15-104">例如，電子郵件使用者會根據「寄件者」訊息與「下列日期之後」訊息來撰寫規則，而保險商業分析師會根據「風險因素」與「保險金額」來撰寫規則。</span><span class="sxs-lookup"><span data-stu-id="fdf15-104">For example, an e-mail user writes rules in terms of messages "received from" and messages "received after," while an insurance business analyst writes rules in terms of "risk factors" and "coverage amount."</span></span>  
  
 <span data-ttu-id="fdf15-105">在此網域特定術語下的是技術成品 (物件、資料庫表格，以及 XML 文件)，可實作規則條件與規則動作。</span><span class="sxs-lookup"><span data-stu-id="fdf15-105">Underlying this domain-specific terminology are the technology artifacts (objects, database tables, and XML documents) that implement rule conditions and rule actions.</span></span> <span data-ttu-id="fdf15-106">Vocabulariesare 設計來橋接商業語意與實作之間的差距。</span><span class="sxs-lookup"><span data-stu-id="fdf15-106">Vocabulariesare designed to bridge the gap between business semantics and implementation.</span></span>  
  
 <span data-ttu-id="fdf15-107">例如，核准狀態的資料繫結有可能指向某個資料庫中某資料列內的某資料欄，以 SQL 查詢表示。</span><span class="sxs-lookup"><span data-stu-id="fdf15-107">For example, a data binding for an approval status might point to a certain column in a certain row in a certain database, represented as an SQL query.</span></span> <span data-ttu-id="fdf15-108">您不需在規則中插入此種的複雜表示法，可改為以「狀態」的易記名稱來建立詞彙定義，並與該資料繫結產生關聯。</span><span class="sxs-lookup"><span data-stu-id="fdf15-108">Instead of inserting this sort of complex representation in a rule, you might instead create a vocabulary definition, associated with that data binding, with a friendly name of "Status."</span></span> <span data-ttu-id="fdf15-109">之後您便可在任何數目的規則中包括「狀態」，而規則引擎可從表格中擷取對應資料。</span><span class="sxs-lookup"><span data-stu-id="fdf15-109">Subsequently you can include "Status" in any number of rules, and the rule engine can retrieve the corresponding data from the table.</span></span>  
  
 <span data-ttu-id="fdf15-110">A*詞彙*是定義規則條件和動作中所用之事實的易記名稱所組成的集合。</span><span class="sxs-lookup"><span data-stu-id="fdf15-110">A *vocabulary* is a collection of definitions consisting of friendly names for the facts used in rule conditions and actions.</span></span> <span data-ttu-id="fdf15-111">詞彙定義讓規則更易於閱讀、瞭解，並可讓特定商業領域的人共用。</span><span class="sxs-lookup"><span data-stu-id="fdf15-111">Vocabulary definitions make the rules easier to read, understand, and share by people in a particular business domain.</span></span>  
  
 <span data-ttu-id="fdf15-112">您可以使用「商務規則編輯器」，定義放置於共用規則存放區中的詞彙。</span><span class="sxs-lookup"><span data-stu-id="fdf15-112">You can use the Business Rule Composer to define vocabularies that are then placed in the shared rule store.</span></span> <span data-ttu-id="fdf15-113">詞彙也可供負責將撰寫規則以整合至新的或現有應用程式的工具開發人員所使用。</span><span class="sxs-lookup"><span data-stu-id="fdf15-113">Vocabularies can also be consumed by tool developers responsible for integrating rule authoring into new or existing applications.</span></span>  
  
 <span data-ttu-id="fdf15-114">在您可以使用詞彙之前，它必須先加上版本的戳記，並發佈於規則存放區中。</span><span class="sxs-lookup"><span data-stu-id="fdf15-114">Before you can use a vocabulary, it must be stamped with a version and published in your rule store.</span></span> <span data-ttu-id="fdf15-115">這可保證詞彙中的定義不會變更，並保留參考的完整性。</span><span class="sxs-lookup"><span data-stu-id="fdf15-115">This is to guarantee that the definitions in the vocabulary will not change, and to preserve referential integrity.</span></span> <span data-ttu-id="fdf15-116">這表示任何使用該特定版本之詞彙的原則，不會因基礎詞彙變更而意外失敗。</span><span class="sxs-lookup"><span data-stu-id="fdf15-116">This means that any policies that use that particular version of the vocabulary will not fail unexpectedly due to changes in the underlying vocabulary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf15-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdf15-117">See Also</span></span>  
 [<span data-ttu-id="fdf15-118">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="fdf15-118">Business Rules Engine</span></span>](../core/business-rules-engine.md)