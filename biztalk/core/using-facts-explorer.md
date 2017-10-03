---
title: "使用 [事實總管] |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Rule Composer, Facts Explorer
- business rules, vocabularies
- business rules, schemas
- business rules, databases
- business rules, .NET classes
- Facts Explorer [Business Rule Composer]
ms.assetid: ee125eb1-d5b9-4121-8a25-fcb7a640570e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4c84b01625bb1566d02c1679bfadd0100b7b406
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-facts-explorer"></a><span data-ttu-id="68140-102">使用 [事實總管]</span><span class="sxs-lookup"><span data-stu-id="68140-102">Using Facts Explorer</span></span>
<span data-ttu-id="68140-103">[事實總管] 包含四個索引標籤：**詞彙**， **XML 結構描述**，**資料庫**，和**.NET 類別**。</span><span class="sxs-lookup"><span data-stu-id="68140-103">The Facts Explorer contains four tabs: **Vocabularies**, **XML Schemas**, **Databases**, and **.NET Classes**.</span></span>  
  
## <a name="vocabularies-tab"></a><span data-ttu-id="68140-104">詞彙索引標籤</span><span class="sxs-lookup"><span data-stu-id="68140-104">Vocabularies tab</span></span>  
 <span data-ttu-id="68140-105">使用**詞彙** 索引標籤管理詞彙版本及定義 事實總管 中的。</span><span class="sxs-lookup"><span data-stu-id="68140-105">Use the **Vocabularies** tab in the Facts Explorer to manage vocabulary versions and definitions.</span></span>  
  
 <span data-ttu-id="68140-106">使用捷徑功能表來存取下列選項。</span><span class="sxs-lookup"><span data-stu-id="68140-106">Use the shortcut menu to access the following options.</span></span>  
  
|<span data-ttu-id="68140-107">使用</span><span class="sxs-lookup"><span data-stu-id="68140-107">Use this</span></span>|<span data-ttu-id="68140-108">動作</span><span class="sxs-lookup"><span data-stu-id="68140-108">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="68140-109">**加入新詞彙**</span><span class="sxs-lookup"><span data-stu-id="68140-109">**Add New Vocabulary**</span></span>|<span data-ttu-id="68140-110">建立新詞彙。</span><span class="sxs-lookup"><span data-stu-id="68140-110">Create a new vocabulary.</span></span>|  
|<span data-ttu-id="68140-111">**加入新的版本**</span><span class="sxs-lookup"><span data-stu-id="68140-111">**Add New Version**</span></span>|<span data-ttu-id="68140-112">建立選取詞彙的新空白版本。</span><span class="sxs-lookup"><span data-stu-id="68140-112">Create a new empty version of the selected vocabulary.</span></span> <span data-ttu-id="68140-113">您可以複製其他版本的定義貼到新版本。</span><span class="sxs-lookup"><span data-stu-id="68140-113">You can copy definitions from other versions and paste them into the new version.</span></span>|  
|<span data-ttu-id="68140-114">**貼上詞彙版本**</span><span class="sxs-lookup"><span data-stu-id="68140-114">**Paste Vocabulary Version**</span></span>|<span data-ttu-id="68140-115">貼上先前複製的詞彙版本內容做為選取詞彙的新版本。</span><span class="sxs-lookup"><span data-stu-id="68140-115">Paste the contents of a previously copied vocabulary version as a new version in the selected vocabulary.</span></span>|  
|<span data-ttu-id="68140-116">**Delete**</span><span class="sxs-lookup"><span data-stu-id="68140-116">**Delete**</span></span>|<span data-ttu-id="68140-117">刪除選取的詞彙及其所有版本。</span><span class="sxs-lookup"><span data-stu-id="68140-117">Delete the selected vocabulary and all its versions.</span></span>|  
|<span data-ttu-id="68140-118">**加入新的定義**</span><span class="sxs-lookup"><span data-stu-id="68140-118">**Add New Definition**</span></span>|<span data-ttu-id="68140-119">啟動 [詞彙定義精靈]，在選取的詞彙版本中建立新定義。</span><span class="sxs-lookup"><span data-stu-id="68140-119">Launch the Vocabulary Definition Wizard to create a new definition in the selected vocabulary version.</span></span>|  
|<span data-ttu-id="68140-120">**儲存**</span><span class="sxs-lookup"><span data-stu-id="68140-120">**Save**</span></span>|<span data-ttu-id="68140-121">儲存對選取詞彙及其定義所作的變更。</span><span class="sxs-lookup"><span data-stu-id="68140-121">Save the changes made to the selected version and its definitions.</span></span>|  
|<span data-ttu-id="68140-122">**發行**</span><span class="sxs-lookup"><span data-stu-id="68140-122">**Publish**</span></span>|<span data-ttu-id="68140-123">發佈選取的詞彙版本。</span><span class="sxs-lookup"><span data-stu-id="68140-123">Publish the selected vocabulary version.</span></span> <span data-ttu-id="68140-124">請注意，您無法直接修改已發佈的版本。</span><span class="sxs-lookup"><span data-stu-id="68140-124">Note that you cannot directly modify a published version.</span></span> <span data-ttu-id="68140-125">您可以複製已發佈的版本並貼到詞彙的新版本。</span><span class="sxs-lookup"><span data-stu-id="68140-125">You can copy and paste it to a new version of the vocabulary.</span></span>|  
|<span data-ttu-id="68140-126">**重新載入**</span><span class="sxs-lookup"><span data-stu-id="68140-126">**Reload**</span></span>|<span data-ttu-id="68140-127">重新載入選取的詞彙版本及其定義，可以選擇是否捨棄對該版本所做的目前變更，並從規則存放區還原其內容。</span><span class="sxs-lookup"><span data-stu-id="68140-127">Reload the selected vocabulary version and its definitions, with the option to discard any current changes made in that version and restore the contents from the rule store.</span></span>|  
|<span data-ttu-id="68140-128">**修改**</span><span class="sxs-lookup"><span data-stu-id="68140-128">**Modify**</span></span>|<span data-ttu-id="68140-129">啟動 [詞彙定義精靈]，變更選取的定義。</span><span class="sxs-lookup"><span data-stu-id="68140-129">Launch the Vocabulary Definition Wizard to change the selected definition.</span></span> <span data-ttu-id="68140-130">請注意，您無法修改屬於已發佈詞彙版本之一部分的定義。</span><span class="sxs-lookup"><span data-stu-id="68140-130">Note that you cannot modify a definition that is part of a published vocabulary version.</span></span>|  
|<span data-ttu-id="68140-131">**移至來源事實**</span><span class="sxs-lookup"><span data-stu-id="68140-131">**Go to source fact**</span></span>|<span data-ttu-id="68140-132">對於選取的定義，請移至 .NET 組件、XML 結構描述或資料庫資料表中的對應來源事實。</span><span class="sxs-lookup"><span data-stu-id="68140-132">For the selected definition, go to the corresponding source fact in a .NET assembly, XML schema, or database table.</span></span>|  
  
## <a name="xml-schemas-tab"></a><span data-ttu-id="68140-133">XML 結構描述索引標籤</span><span class="sxs-lookup"><span data-stu-id="68140-133">XML Schemas tab</span></span>  
 <span data-ttu-id="68140-134">瀏覽 XSD 結構描述尋找 XML 項目和屬性的定義。</span><span class="sxs-lookup"><span data-stu-id="68140-134">Browse through XSD schemas for the definitions of XML elements and attributes.</span></span> <span data-ttu-id="68140-135">您可以拖曳項目拖曳至未發佈的詞彙版本上**詞彙**索引標籤上，以建立定義，或您可以將項目拖曳到條件編輯器或動作編輯器，以定義述詞、 動作和引數。</span><span class="sxs-lookup"><span data-stu-id="68140-135">You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.</span></span>  
  
|<span data-ttu-id="68140-136">使用</span><span class="sxs-lookup"><span data-stu-id="68140-136">Use this</span></span>|<span data-ttu-id="68140-137">動作</span><span class="sxs-lookup"><span data-stu-id="68140-137">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="68140-138">**選取根節點**</span><span class="sxs-lookup"><span data-stu-id="68140-138">**Select Root Node**</span></span>|<span data-ttu-id="68140-139">選取要從包含多個根節點的 XML 結構描述載入的根節點。</span><span class="sxs-lookup"><span data-stu-id="68140-139">Select a root node to load from an XML schema that contains multiple root notes.</span></span>|  
  
## <a name="databases-tab"></a><span data-ttu-id="68140-140">資料庫索引標籤</span><span class="sxs-lookup"><span data-stu-id="68140-140">Databases tab</span></span>  
 <span data-ttu-id="68140-141">瀏覽資料庫伺服器尋找資料庫和資料表定義。</span><span class="sxs-lookup"><span data-stu-id="68140-141">Browse through database servers for databases and table definitions.</span></span> <span data-ttu-id="68140-142">您可以拖曳項目拖曳至未發佈的詞彙版本上**詞彙**索引標籤上，以建立定義，或您可以將項目拖曳到條件編輯器或動作編輯器，以定義述詞、 動作和引數。</span><span class="sxs-lookup"><span data-stu-id="68140-142">You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.</span></span>  
  
## <a name="net-classes-tab"></a><span data-ttu-id="68140-143">.NET 類別索引標籤</span><span class="sxs-lookup"><span data-stu-id="68140-143">.NET Classes tab</span></span>  
 <span data-ttu-id="68140-144">瀏覽 .NET 組件尋找 .NET 公開類別定義。</span><span class="sxs-lookup"><span data-stu-id="68140-144">Browse through .NET assemblies for public .NET class definitions.</span></span> <span data-ttu-id="68140-145">您可以拖曳項目拖曳至未發佈的詞彙版本上**詞彙**索引標籤上，以建立定義，或您可以將項目拖曳到條件編輯器或動作編輯器，以定義述詞、 動作和引數。</span><span class="sxs-lookup"><span data-stu-id="68140-145">You can drag items onto unpublished vocabulary versions on the **Vocabulary** tab to create definitions, or you can drag items to the Conditions Editor or Actions Editor to define predicates, actions, and arguments.</span></span>  
  
|<span data-ttu-id="68140-146">使用</span><span class="sxs-lookup"><span data-stu-id="68140-146">Use this</span></span>|<span data-ttu-id="68140-147">動作</span><span class="sxs-lookup"><span data-stu-id="68140-147">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="68140-148">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="68140-148">**Browse**</span></span>|<span data-ttu-id="68140-149">從全域組件快取載入 .NET 組件</span><span class="sxs-lookup"><span data-stu-id="68140-149">Load a .NET assembly from the global assembly cache</span></span>|  
|<span data-ttu-id="68140-150">**移除**</span><span class="sxs-lookup"><span data-stu-id="68140-150">**Remove**</span></span>|<span data-ttu-id="68140-151">移除 .NET 組件</span><span class="sxs-lookup"><span data-stu-id="68140-151">Remove a .NET assembly</span></span>|