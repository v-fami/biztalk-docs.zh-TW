---
title: 表格驅動迴圈組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Table Looping functoids
- Table Extractor functoids, configuring
- Table Extractor functoids
- Table Extractor functoids, adding to grid
- Table Looping functoids, about Table Looping functoids
- Table Looping functoids, configuring
- Table Extractor functoids, about Table Extractor functoids
- Table Looping functoids, adding to map
ms.assetid: ecc24d9b-ebc0-4559-9746-58e3b00c02ab
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6030c721207e5b7f2c9958a50758c0ed98097c8d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973932"
---
# <a name="table-driven-looping-configuration"></a><span data-ttu-id="4aa8f-102">表格驅動迴圈組態</span><span class="sxs-lookup"><span data-stu-id="4aa8f-102">Table-Driven Looping Configuration</span></span>
<span data-ttu-id="4aa8f-103">依照下列步驟設定對應中的表格驅動迴圈：</span><span class="sxs-lookup"><span data-stu-id="4aa8f-103">Follow these steps to configure table-driven looping in your map:</span></span>  
  
-   <span data-ttu-id="4aa8f-104">**新增表格迴圈運算質至對應。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-104">**Add a Table Looping functoid to the map.**</span></span> <span data-ttu-id="4aa8f-105">您只需要一個**表格迴圈**運算質，每個表格驅動迴圈的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-105">You need only one **Table Looping** functoid per table-driven looping instance.</span></span> <span data-ttu-id="4aa8f-106">例如，如果您使用表格驅動迴圈來衍生 BillTo 和 ShipTo 資訊，您只需要一個**表格迴圈**對應中的運算質。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-106">For example, if you are using table-driven looping to derive BillTo and ShipTo information, you need only one **Table Looping** functoid in your map.</span></span> <span data-ttu-id="4aa8f-107">不過，如果您使用表格驅動迴圈來衍生 BillTo 和 ShipTo 資訊以及 StoreName 和 StoreAddress 資訊，您可能需要兩個**表格迴圈**對應中的運算質。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-107">However, if you are using table-driven looping to derive BillTo and ShipTo information and StoreName and StoreAddress information, you might need two **Table Looping** functoids in your map.</span></span>  
  
-   <span data-ttu-id="4aa8f-108">**顯示的格線頁中加入一個詳細的表格抽選程式運算質。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-108">**Add one more Table Extractor functoid to the displayed grid page.**</span></span> <span data-ttu-id="4aa8f-109">加入做為許多**表格抽選程式**做為您的運算質需要每個**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-109">Add as many **Table Extractor** functoids as you need for each **Table Looping** functoid.</span></span> <span data-ttu-id="4aa8f-110">數目**表格抽選程式**運算質的目的結構描述中的欄位數目而定。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-110">The number of **Table Extractor** functoids depends on the number of fields in the destination schema.</span></span> <span data-ttu-id="4aa8f-111">例如，如果您只需要**AddressCode**在您來源結構描述和公司名稱、 地址、 縣 （市）、 狀態、 郵遞區號和 AttentionName 目的地結構描述中的，您需要新增 6 個**表格抽選程式**若要顯示的格線頁的運算質。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-111">For example, if you only have an **AddressCode** in your source schema and CompanyName, Address, City, State, PostalCode, and AttentionName in your destination schema, you need to add six **Table Extractor** functoids to the displayed grid page.</span></span>  
  
-   <span data-ttu-id="4aa8f-112">**以適當輸入設定表格迴圈運算質。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-112">**Configure the Table Looping functoid with the appropriate inputs.**</span></span> <span data-ttu-id="4aa8f-113">首先，連結**表格迴圈**運算質到輸入執行個體記錄或項目。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-113">First, link the **Table Looping** functoid to the input instance record or element.</span></span> <span data-ttu-id="4aa8f-114">並將它連結到輸出執行個體訊息中的結構。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-114">Also link it to the structure in the output instance message.</span></span> <span data-ttu-id="4aa8f-115">接下來，使用設定輸入**設定\<運算質\>運算質** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-115">Next, configure the inputs by using the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="4aa8f-116">如需如何設定這個屬性的詳細資訊，請參閱[編輯運算質屬性和輸入參數](../core/editing-functoid-properties-and-input-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-116">For more information about how to configure this property, see [Editing Functoid Properties and Input Parameters](../core/editing-functoid-properties-and-input-parameters.md) .</span></span> <span data-ttu-id="4aa8f-117">您輸入的輸入清單必須是完整且完整，因為這是您用來設定資料**資料表運算質方格**屬性。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-117">The list of inputs you enter must be comprehensive and complete because this is the data that you will use to configure the **Table Functoid Grid** property.</span></span> <span data-ttu-id="4aa8f-118">這些輸入必須定義如下：</span><span class="sxs-lookup"><span data-stu-id="4aa8f-118">The inputs must be defined as follows:</span></span>  
  
    -   <span data-ttu-id="4aa8f-119">**第一個輸入。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-119">**First input.**</span></span> <span data-ttu-id="4aa8f-120">第一個輸入參數連接到輸入執行個體訊息記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-120">The first input parameter is the link to the input instance message record or field.</span></span> <span data-ttu-id="4aa8f-121">**表格迴圈**運算質都重複一次的記錄或欄位的每個執行個體。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-121">The **Table Looping** functoid loops once for each instance of the record or field.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4aa8f-122">這是必要的輸入。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-122">This is a required input.</span></span>  
  
    -   <span data-ttu-id="4aa8f-123">**第二個輸入。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-123">**Second input.**</span></span> <span data-ttu-id="4aa8f-124">第二個輸入參數定義迴圈格線中的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-124">The second input parameter defines the number of columns in the looping grid.</span></span> <span data-ttu-id="4aa8f-125">此格線最多可包含 228 個資料行。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-125">The grid may contain up to 228 columns.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4aa8f-126">這是必要的輸入。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-126">This is a required input.</span></span>  
  
    -   <span data-ttu-id="4aa8f-127">**其餘輸入。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-127">**Remaining inputs.**</span></span> <span data-ttu-id="4aa8f-128">其餘的輸入**表格迴圈**運算質所組成的所有可能的值，可能會出現在清單**資料表運算質方格**。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-128">The remaining inputs for the **Table Looping** functoid consist of a list of all of the possible values that may appear in the **Table Functoid Grid**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="4aa8f-129">標籤連結非常有用。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-129">Labeling links is very helpful.</span></span> <span data-ttu-id="4aa8f-130">標籤、 連結會出現在**資料表運算質方格**為完整指定路徑。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-130">Without labels, links appear in the **Table Functoid Grid** as fully specified paths.</span></span>  
  
         <span data-ttu-id="4aa8f-131">如需如何設定輸入的逐步指示**表格迴圈**運算質，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-131">For step-by-step instructions about how to configure inputs for the **Table Looping** functoid, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).</span></span> <span data-ttu-id="4aa8f-132">請特別參閱步驟 3 到 8。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-132">In particular, see steps 3 through 8.</span></span>  
  
-   <span data-ttu-id="4aa8f-133">**設定表格迴圈運算質的運算質在資料表方格屬性。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-133">**Configure the Table Functoid Grid property of the Table Looping functoid.**</span></span> <span data-ttu-id="4aa8f-134">使用**資料表運算質方格**屬性可開啟**設定表格迴圈運算質**對話方塊中，您可以在其中設定迴圈格線中的資料格。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-134">Use the **Table Functoid Grid** property to open the **Configure Table Looping Functoid** dialog box in which you configure the cells in the looping grid.</span></span>  
  
     <span data-ttu-id="4aa8f-135">如需有關如何設定迴圈格線的逐步指示，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-135">For step-by-step instructions about how to configure the looping grid, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).</span></span> <span data-ttu-id="4aa8f-136">請特別參閱步驟 9 和 10。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-136">In particular, see steps 9 and 10.</span></span>  
  
-   <span data-ttu-id="4aa8f-137">**設定表格抽選程式運算質。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-137">**Configure the Table Extractor functoids.**</span></span> <span data-ttu-id="4aa8f-138">使用**輸入參數**屬性可設定**表格抽選程式**運算質的輸入，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4aa8f-138">Use the **Input Parameters** property to configure the **Table Extractor** functoid inputs as follows:</span></span>  
  
    -   <span data-ttu-id="4aa8f-139">**第一個輸入。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-139">**First input.**</span></span> <span data-ttu-id="4aa8f-140">第一個輸入的參數**表格抽選程式**運算質是**表格迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-140">The first input parameter to a **Table Extractor** functoid is the **Table Looping** functoid.</span></span>  
  
    -   <span data-ttu-id="4aa8f-141">**第二個輸入。**</span><span class="sxs-lookup"><span data-stu-id="4aa8f-141">**Second input.**</span></span> <span data-ttu-id="4aa8f-142">第二個輸入參數指定要擷取資料的資料列中的資料行。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-142">The second input parameter specifies the column in the row from which to extract data.</span></span>  
  
     <span data-ttu-id="4aa8f-143">如需如何設定逐步指示**表格抽選程式**與相關聯的運算質**表格迴圈**運算質，請參閱[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md)。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-143">For step-by-step instructions about how to configure the **Table Extractor** functoids associated with a **Table Looping** functoid, see [How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md).</span></span> <span data-ttu-id="4aa8f-144">特別是，請參閱步驟 11 至 16。</span><span class="sxs-lookup"><span data-stu-id="4aa8f-144">In particular, see steps 11 through 16.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa8f-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="4aa8f-145">See Also</span></span>  
 <span data-ttu-id="4aa8f-146">[表格迴圈運算質](../core/table-looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-146">[Table Looping Functoid](../core/table-looping-functoid.md) </span></span>  
 <span data-ttu-id="4aa8f-147">[表格抽選程式運算質](../core/table-extractor-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-147">[Table Extractor Functoid](../core/table-extractor-functoid.md) </span></span>  
 <span data-ttu-id="4aa8f-148">[表格驅動迴圈範例](../core/table-driven-looping-example.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-148">[Table-Driven Looping Example](../core/table-driven-looping-example.md) </span></span>  
 <span data-ttu-id="4aa8f-149">[如何新增表格迴圈和表格擷取程式運算質至對應](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-149">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="4aa8f-150">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-150">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="4aa8f-151">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-151">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="4aa8f-152">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-152">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="4aa8f-153">[迴圈運算質](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="4aa8f-153">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="4aa8f-154">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="4aa8f-154">Record Count Functoid</span></span>](../core/record-count-functoid.md)