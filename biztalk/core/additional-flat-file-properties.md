---
title: 其他一般檔案屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c88ad2f-b5a8-46e6-b1b8-61ce6ba910d1
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56db18d93eda3c5ddaaefcf58b73e0870cbb332c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013311"
---
# <a name="additional-flat-file-properties"></a><span data-ttu-id="3773e-102">其他一般檔案屬性</span><span class="sxs-lookup"><span data-stu-id="3773e-102">Additional Flat File Properties</span></span>

## <a name="hidden-properties"></a><span data-ttu-id="3773e-103">隱藏的屬性</span><span class="sxs-lookup"><span data-stu-id="3773e-103">Hidden properties</span></span>
<span data-ttu-id="3773e-104">下表列出「結構描述編輯器」中未顯示的其他一般檔案節點屬性。</span><span class="sxs-lookup"><span data-stu-id="3773e-104">The following table lists additional flat file node properties that do not appear in the Schema Editor.</span></span> <span data-ttu-id="3773e-105">若要使用這些屬性，需要在文字編輯器中手動編輯結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="3773e-105">Using these properties requires hand editing the schema file in a text editor.</span></span>  

|<span data-ttu-id="3773e-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3773e-106">Property</span></span>|<span data-ttu-id="3773e-107">值</span><span class="sxs-lookup"><span data-stu-id="3773e-107">Values</span></span>|<span data-ttu-id="3773e-108">預設值</span><span class="sxs-lookup"><span data-stu-id="3773e-108">Default Value</span></span>|<span data-ttu-id="3773e-109">描述</span><span class="sxs-lookup"><span data-stu-id="3773e-109">Description</span></span>|  
|--------------|------------|-------------------|-----------------|  
|<span data-ttu-id="3773e-110">suppress_empty_nodes</span><span class="sxs-lookup"><span data-stu-id="3773e-110">suppress_empty_nodes</span></span>|<span data-ttu-id="3773e-111">**[True]** 或 **[False]**</span><span class="sxs-lookup"><span data-stu-id="3773e-111">**true** or **false**</span></span>|<span data-ttu-id="3773e-112">**false**</span><span class="sxs-lookup"><span data-stu-id="3773e-112">**false**</span></span>|<span data-ttu-id="3773e-113">指示在剖析器產生 XML 執行個體資料後是否移除空的 XML 節點。</span><span class="sxs-lookup"><span data-stu-id="3773e-113">Indicates whether or not to remove empty XML nodes after the parser generates XML instance data.</span></span>|  
|<span data-ttu-id="3773e-114">generate_empty_nodes</span><span class="sxs-lookup"><span data-stu-id="3773e-114">generate_empty_nodes</span></span>|<span data-ttu-id="3773e-115">**[True]** 或 **[False]**</span><span class="sxs-lookup"><span data-stu-id="3773e-115">**true** or **false**</span></span>|<span data-ttu-id="3773e-116">**true**</span><span class="sxs-lookup"><span data-stu-id="3773e-116">**true**</span></span>|<span data-ttu-id="3773e-117">為存在 XML 執行個體資料中的記錄產生空節點。</span><span class="sxs-lookup"><span data-stu-id="3773e-117">Generate empty nodes for records that exist in the XML instance data.</span></span>|  
|<span data-ttu-id="3773e-118">parser_optimization</span><span class="sxs-lookup"><span data-stu-id="3773e-118">parser_optimization</span></span>|<span data-ttu-id="3773e-119">**速度**或**複雜度**</span><span class="sxs-lookup"><span data-stu-id="3773e-119">**speed** or **complexity**</span></span>|<span data-ttu-id="3773e-120">**速度**</span><span class="sxs-lookup"><span data-stu-id="3773e-120">**speed**</span></span>|<span data-ttu-id="3773e-121">使速度最佳化可降低剖析時間，但代價是必須處理一些不明確的資料。</span><span class="sxs-lookup"><span data-stu-id="3773e-121">Optimizing for speed decreases the parsing time but at the cost of dealing with some ambiguities in data.</span></span> <span data-ttu-id="3773e-122">使複雜度最佳化可處理範圍較廣的模稜兩可狀況，但會犧牲速度。</span><span class="sxs-lookup"><span data-stu-id="3773e-122">Optimizing for complexity handles a wider range of ambiguities but at the cost of processing speed.</span></span>|  
|<span data-ttu-id="3773e-123">lookahead_depth</span><span class="sxs-lookup"><span data-stu-id="3773e-123">lookahead_depth</span></span>|<span data-ttu-id="3773e-124">任何正整數；零 (0) 表示無限先行剖析。</span><span class="sxs-lookup"><span data-stu-id="3773e-124">Any positive integer; zero (0) indicates infinite lookahead.</span></span>|<span data-ttu-id="3773e-125">3</span><span class="sxs-lookup"><span data-stu-id="3773e-125">3</span></span>|<span data-ttu-id="3773e-126">比對資料的先行剖析深度。</span><span class="sxs-lookup"><span data-stu-id="3773e-126">How far to look ahead for matching data.</span></span>|  
|<span data-ttu-id="3773e-127">allow_early_termination</span><span class="sxs-lookup"><span data-stu-id="3773e-127">allow_early_termination</span></span>|<span data-ttu-id="3773e-128">**[True]** 或 **[False]**</span><span class="sxs-lookup"><span data-stu-id="3773e-128">**true** or **false**</span></span>|<span data-ttu-id="3773e-129">**false**</span><span class="sxs-lookup"><span data-stu-id="3773e-129">**false**</span></span>|<span data-ttu-id="3773e-130">指出是否可提早終止位置記錄 (**，則為 true**)，或必須包含所有記錄欄位的資料 (**false**)。</span><span class="sxs-lookup"><span data-stu-id="3773e-130">Indicates whether positional records can terminate early (**true**) or must contain data for all record fields (**false**).</span></span>|  
|<span data-ttu-id="3773e-131">early_terminate_optional_fields</span><span class="sxs-lookup"><span data-stu-id="3773e-131">early_terminate_optional_fields</span></span>|<span data-ttu-id="3773e-132">**[True]** 或 **[False]**</span><span class="sxs-lookup"><span data-stu-id="3773e-132">**true** or **false**</span></span>|<span data-ttu-id="3773e-133">**false**</span><span class="sxs-lookup"><span data-stu-id="3773e-133">**false**</span></span>|<span data-ttu-id="3773e-134">讓選擇性尾端欄位提早終止 (**，則為 true**)。</span><span class="sxs-lookup"><span data-stu-id="3773e-134">Enable early termination of optional trailing fields (**true**).</span></span> <span data-ttu-id="3773e-135">如果在 BizTalk 編輯器中開啟現有的結構描述，如果沒有此註解，此註解會將它設為預設值 (**false**)。</span><span class="sxs-lookup"><span data-stu-id="3773e-135">If the existing schema without this annotation is opened in the BizTalk Editor, this annotation will be added to it with the default value set to (**false**).</span></span> <span data-ttu-id="3773e-136">**注意：** early_terminate_optional_fields 註解才會生效，如果在 allow_early_termination 設定為"true"。</span><span class="sxs-lookup"><span data-stu-id="3773e-136">**Note:**  The early_terminate_optional_fields annotation only takes effect if the allow_early_termination is set to "true".</span></span>|  

 <span data-ttu-id="3773e-137">所有這些屬性是的特性 **/annotation/appinfo/schemaInfo**項目。</span><span class="sxs-lookup"><span data-stu-id="3773e-137">All of these properties are attributes of the **/annotation/appinfo/schemaInfo** element.</span></span>  

 <span data-ttu-id="3773e-138">當**parser_optimization**設為**複雜度**，有相同的群組或記錄中的許多選擇性節點時，您可能必須針對結構描述驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="3773e-138">When **parser_optimization** is set to **complexity**, you may have validation failures against a schema when there are many optional nodes in the same group or record.</span></span> <span data-ttu-id="3773e-139">您可能需要設定**lookahead_depth**為零 (0) 以避免驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="3773e-139">You may need to set **lookahead_depth** to zero (0) to avoid validation errors.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3773e-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3773e-140">See Also</span></span>  
- [<span data-ttu-id="3773e-141">節點屬性</span><span class="sxs-lookup"><span data-stu-id="3773e-141">Node Properties</span></span>](../core/node-properties.md)   
- <span data-ttu-id="3773e-142">**一般檔案結構描述的增補節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="3773e-142">**Supplemental Node Properties for Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
