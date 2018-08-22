---
title: 資料庫運算質 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 77bc9390-cdb5-42ff-8b28-6265c51c79fc
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d5c0b1be12176653bba2414e32bdefbd83e9083
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013831"
---
# <a name="database-functoids"></a><span data-ttu-id="1a916-102">資料庫運算質</span><span class="sxs-lookup"><span data-stu-id="1a916-102">Database Functoids</span></span>
<span data-ttu-id="1a916-103">**資料庫**運算質擷取輸出執行個體訊息中使用的資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="1a916-103">**Database** functoids extract data from a database for use in an output instance message.</span></span> 

## <a name="overview"></a><span data-ttu-id="1a916-104">概觀</span><span class="sxs-lookup"><span data-stu-id="1a916-104">Overview</span></span>
<span data-ttu-id="1a916-105">以下是一份**資料庫**運算質，並使用它們：</span><span class="sxs-lookup"><span data-stu-id="1a916-105">The following is a list of the **Database** functoids and how you can use them:</span></span>  

- <span data-ttu-id="1a916-106">**資料庫尋查。**</span><span class="sxs-lookup"><span data-stu-id="1a916-106">**Database Lookup.**</span></span> <span data-ttu-id="1a916-107">使用**資料庫查閱**」 運算質，從資料庫擷取資訊，並將它儲存為 Microsoft ActiveX Data Objects.NET (ADO.NET) 資料錄集。</span><span class="sxs-lookup"><span data-stu-id="1a916-107">Use the **Database Lookup** functoid to extract information from a database and store it as a Microsoft ActiveX Data Objects .NET (ADO.NET) recordset.</span></span> <span data-ttu-id="1a916-108">此運算質需要四個依照下列順序的輸入參數：</span><span class="sxs-lookup"><span data-stu-id="1a916-108">This functoid requires four input parameters in the following order:</span></span>  

  -   <span data-ttu-id="1a916-109">尋查值</span><span class="sxs-lookup"><span data-stu-id="1a916-109">A lookup value</span></span>  

  -   <span data-ttu-id="1a916-110">資料庫連接字串</span><span class="sxs-lookup"><span data-stu-id="1a916-110">A database connection string</span></span>  

  -   <span data-ttu-id="1a916-111">資料表名稱</span><span class="sxs-lookup"><span data-stu-id="1a916-111">A table name</span></span>  

  -   <span data-ttu-id="1a916-112">尋查值的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="1a916-112">A column name for the lookup value.</span></span>  

- <span data-ttu-id="1a916-113">**錯誤傳回。**</span><span class="sxs-lookup"><span data-stu-id="1a916-113">**Error Return.**</span></span> <span data-ttu-id="1a916-114">使用**錯誤傳回**」 運算質擷取錯誤的相關資訊，例如資料庫連線失敗，在執行階段發生。</span><span class="sxs-lookup"><span data-stu-id="1a916-114">Use the **Error Return** functoid to capture error information, such as database connection failures, that occur during run time.</span></span> <span data-ttu-id="1a916-115">此運算質需要一個輸入的參數： 的連結**資料庫查閱**運算質。</span><span class="sxs-lookup"><span data-stu-id="1a916-115">This functoid requires one input parameter: a link from the **Database Lookup** functoid.</span></span>  

- <span data-ttu-id="1a916-116">**格式訊息。**</span><span class="sxs-lookup"><span data-stu-id="1a916-116">**Format Message.**</span></span> <span data-ttu-id="1a916-117">使用引數替代，也可能使用識別碼和交互參照值，傳回格式化和當地語系化的字串。</span><span class="sxs-lookup"><span data-stu-id="1a916-117">Returns a formatted and localized string using argument substitution and, potentially, ID and value cross-referencing.</span></span>  

- <span data-ttu-id="1a916-118">**取得應用程式識別碼。**</span><span class="sxs-lookup"><span data-stu-id="1a916-118">**Get Application ID.**</span></span> <span data-ttu-id="1a916-119">擷取應用程式物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1a916-119">Retrieves an identifier for an application object.</span></span>  

- <span data-ttu-id="1a916-120">**取得應用程式值。**</span><span class="sxs-lookup"><span data-stu-id="1a916-120">**Get Application Value.**</span></span> <span data-ttu-id="1a916-121">擷取應用程式值。</span><span class="sxs-lookup"><span data-stu-id="1a916-121">Retrieves an application value.</span></span>  

- <span data-ttu-id="1a916-122">**取得通用識別碼。**</span><span class="sxs-lookup"><span data-stu-id="1a916-122">**Get Common ID.**</span></span> <span data-ttu-id="1a916-123">擷取通用物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1a916-123">Retrieves an identifier for a common object.</span></span>  

- <span data-ttu-id="1a916-124">**取得通用值。**</span><span class="sxs-lookup"><span data-stu-id="1a916-124">**Get Common Value.**</span></span> <span data-ttu-id="1a916-125">擷取通用值。</span><span class="sxs-lookup"><span data-stu-id="1a916-125">Retrieves a common value.</span></span>  

- <span data-ttu-id="1a916-126">**移除應用程式識別碼。**</span><span class="sxs-lookup"><span data-stu-id="1a916-126">**Remove Application ID.**</span></span> <span data-ttu-id="1a916-127">移除應用程式值。</span><span class="sxs-lookup"><span data-stu-id="1a916-127">Removes an application value.</span></span>  

- <span data-ttu-id="1a916-128">**設定通用識別碼。**</span><span class="sxs-lookup"><span data-stu-id="1a916-128">**Set Common ID.**</span></span> <span data-ttu-id="1a916-129">設定和傳回通用物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="1a916-129">Sets and returns an identifier for a common object.</span></span>  

- <span data-ttu-id="1a916-130">**值擷取程式 」。**</span><span class="sxs-lookup"><span data-stu-id="1a916-130">**Value Extractor.**</span></span> <span data-ttu-id="1a916-131">使用**Value Extractor**從指定的資料行中所傳回的資料錄集擷取資料的運算質**資料庫尋查**運算質。</span><span class="sxs-lookup"><span data-stu-id="1a916-131">Use the **Value Extractor** functoid to extract data from the specified column in a recordset returned by the **Database Lookup** functoid.</span></span> <span data-ttu-id="1a916-132">此運算質需要兩個輸入參數： 通往**資料庫查閱**運算質和資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="1a916-132">This functoid requires two input parameters: a link to the **Database Lookup** functoid and a column name.</span></span>  

  <span data-ttu-id="1a916-133">七**資料庫**運算質 —**格式的訊息、 取得應用程式識別碼**，**取得應用程式值**，**取得通用識別碼**， **取得通用值**，**移除應用程式識別碼**，和**設定通用識別碼**— 會**CrossReferencing**運算質。</span><span class="sxs-lookup"><span data-stu-id="1a916-133">Seven of the **Database** functoids— **Format Message, Get Application ID**, **Get Application Value**, **Get Common ID**, **Get Common Value**, **Remove Application ID**, and **Set Common ID**—are **CrossReferencing** functoids.</span></span> <span data-ttu-id="1a916-134">這些運算質會將輸入訊息的識別碼和值轉譯為輸出訊息所需的識別碼和值。</span><span class="sxs-lookup"><span data-stu-id="1a916-134">These functoids translate IDs and values from an input message into the IDs and values needed in the output message.</span></span> <span data-ttu-id="1a916-135">如需詳細資訊，請參閱 <<c0>  **資料庫運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="1a916-135">For more information, see **Database Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 

## <a name="example"></a><span data-ttu-id="1a916-136">範例</span><span class="sxs-lookup"><span data-stu-id="1a916-136">Example</span></span>  
 <span data-ttu-id="1a916-137">下列範例使用的一些**資料庫**運算質。</span><span class="sxs-lookup"><span data-stu-id="1a916-137">The following example uses some of the **Database** functoids.</span></span> <span data-ttu-id="1a916-138">假設一個大型零售製造商有遍佈各地的門市。</span><span class="sxs-lookup"><span data-stu-id="1a916-138">Consider a large retail manufacturer with stores spread over a large geographical area.</span></span> <span data-ttu-id="1a916-139">要追蹤存放區，總部指派唯一的程式碼呼叫每個存放區**StoreID**。</span><span class="sxs-lookup"><span data-stu-id="1a916-139">To keep track of the stores, headquarters assigns each store a unique code called a **StoreID**.</span></span> <span data-ttu-id="1a916-140">此外，總部將以下資訊與每個**StoreID**:</span><span class="sxs-lookup"><span data-stu-id="1a916-140">Additionally, headquarters associates the following information with each **StoreID**:</span></span>  

- <span data-ttu-id="1a916-141">StoreName</span><span class="sxs-lookup"><span data-stu-id="1a916-141">StoreName</span></span>  

- <span data-ttu-id="1a916-142">StoreAddress</span><span class="sxs-lookup"><span data-stu-id="1a916-142">StoreAddress</span></span>  

- <span data-ttu-id="1a916-143">[縣/市]</span><span class="sxs-lookup"><span data-stu-id="1a916-143">City</span></span>  

- <span data-ttu-id="1a916-144">PostalCode</span><span class="sxs-lookup"><span data-stu-id="1a916-144">PostalCode</span></span>  

- <span data-ttu-id="1a916-145">StorePhoneNumber</span><span class="sxs-lookup"><span data-stu-id="1a916-145">StorePhoneNumber</span></span>  

- <span data-ttu-id="1a916-146">StoreManager</span><span class="sxs-lookup"><span data-stu-id="1a916-146">StoreManager</span></span>  

  <span data-ttu-id="1a916-147">此資訊儲存在資料庫中並定期散發給交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="1a916-147">This information is stored in a database and is distributed to trading partners on a regular basis.</span></span> <span data-ttu-id="1a916-148">對於製造商而言，所有採購是由總部完成，而非門市。</span><span class="sxs-lookup"><span data-stu-id="1a916-148">For the manufacturer, all purchasing is done by headquarters, not the stores.</span></span> <span data-ttu-id="1a916-149">當總部寄送訂單給交易夥伴時，多家門市收到單一訂單所訂購的商品是很平常的。</span><span class="sxs-lookup"><span data-stu-id="1a916-149">When headquarters sends a purchase order to the trading partners, it is common for multiple stores to receive merchandise ordered through the single purchase order.</span></span> <span data-ttu-id="1a916-150">而不是傳送要接收商品的每個存放區的名稱和位址資訊，總部只傳送**StoreID**。</span><span class="sxs-lookup"><span data-stu-id="1a916-150">Instead of sending name and address information for each store that is to receive merchandise, headquarters simply sends the **StoreID**.</span></span> <span data-ttu-id="1a916-151">若要將名稱和位址資訊插入進階的交貨通知，交易夥伴會使用**資料庫**運算質可自動插入輸出執行個體訊息中的這項資訊。</span><span class="sxs-lookup"><span data-stu-id="1a916-151">To insert the name and address information into the advanced ship notice, the trading partner uses the **Database** functoids to automatically insert this information into the output instance message.</span></span> <span data-ttu-id="1a916-152">下圖顯示交易夥伴如何在對應中實作 StoreID 的取代。</span><span class="sxs-lookup"><span data-stu-id="1a916-152">The following figure shows how a trading partner can implement the replacement of the StoreID in a map.</span></span>  

  <span data-ttu-id="1a916-153">![將顯示不同資料庫運算質的對應。](../core/media/origdbfunctoids.gif "origdbfunctoids")</span><span class="sxs-lookup"><span data-stu-id="1a916-153">![Map showing  different database functoids.](../core/media/origdbfunctoids.gif "origdbfunctoids")</span></span>  

  <span data-ttu-id="1a916-154">在圖中，來源結構描述代表內送訂單，而目的結構描述代表進階交貨通知。</span><span class="sxs-lookup"><span data-stu-id="1a916-154">In the figure, the source schema represents an incoming purchase order; the destination schema represents an advanced ship notice.</span></span> <span data-ttu-id="1a916-155">**資料庫查閱**運算質會尋找適當的記錄，從適當的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="1a916-155">The **Database Lookup** functoid finds the appropriate record from the appropriate database table.</span></span> <span data-ttu-id="1a916-156">**Value Extractor**運算質從尋查記錄擷取適當的資料行。</span><span class="sxs-lookup"><span data-stu-id="1a916-156">The **Value Extractor** functoids extract the appropriate column from the lookup record.</span></span> <span data-ttu-id="1a916-157">**錯誤傳回**運算質會輸出字串，包含錯誤的資訊，如果發生錯誤 （例如連接失敗），在執行階段。</span><span class="sxs-lookup"><span data-stu-id="1a916-157">The **Error Return** functoid outputs a string containing error information if there are errors (such as connection failures) at run time.</span></span>  

  <span data-ttu-id="1a916-158">在上述範例中，第一個輸入的參數取自**StoreID**欄位內送的購買訂單，而其餘三個輸入的參數會設定中的常數**設定\<運算質\>運算質** 對話方塊**資料庫尋查**運算質。</span><span class="sxs-lookup"><span data-stu-id="1a916-158">In the previous example, the first input parameter is taken from the **StoreID** field of the incoming purchase order, and the remaining three input parameters are constants configured in the **Configure \<Functoid\> Functoid** dialog box for the **Database Lookup** functoid.</span></span> <span data-ttu-id="1a916-159">也可以從來源結構描述建立連結，為所有四個輸入參數提供值。</span><span class="sxs-lookup"><span data-stu-id="1a916-159">It is possible to create links from the source schema to supply values for all four input parameters.</span></span>  

> [!NOTE]
>  * <span data-ttu-id="1a916-160">您無法使用某些 Microsoft SQL Server 資料類型，例如**文字**， **ntext**，並**映像**，作為查閱值**資料庫尋查**運算質。</span><span class="sxs-lookup"><span data-stu-id="1a916-160">You cannot use some Microsoft SQL Server data types, such as **text**, **ntext**, and **image**, as lookup values for the **Database Lookup** functoid.</span></span> <span data-ttu-id="1a916-161">運算質需要可用文字字串表示的資料型別。</span><span class="sxs-lookup"><span data-stu-id="1a916-161">The functoid requires data types that can be represented as a text string.</span></span>  
>
>  * <span data-ttu-id="1a916-162">是否有相符的輸入的參數的多個資料錄**資料庫尋查**運算質**值擷取程式 」** 運算質只會從第一筆記錄會擷取資料。</span><span class="sxs-lookup"><span data-stu-id="1a916-162">If there is more than one record matching the input parameters of the **Database Lookup** functoid, the **Value Extractor** functoid extracts data only from the first record.</span></span>  
>
>  * <span data-ttu-id="1a916-163">使用 NT 驗證連接字串保護加密的密碼。</span><span class="sxs-lookup"><span data-stu-id="1a916-163">Use NT authentication in connection strings to protect passwords with encryption.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="1a916-164">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="1a916-164">Available functoids</span></span>  
 <span data-ttu-id="1a916-165">**資料庫**運算質為：</span><span class="sxs-lookup"><span data-stu-id="1a916-165">The **Database** functoids are:</span></span> 

* <span data-ttu-id="1a916-166">資料庫尋查</span><span class="sxs-lookup"><span data-stu-id="1a916-166">Database Lookup</span></span>
* <span data-ttu-id="1a916-167">錯誤傳回</span><span class="sxs-lookup"><span data-stu-id="1a916-167">Error Return</span></span>
* <span data-ttu-id="1a916-168">格式訊息</span><span class="sxs-lookup"><span data-stu-id="1a916-168">Format Message</span></span>
* <span data-ttu-id="1a916-169">取得應用程式識別碼</span><span class="sxs-lookup"><span data-stu-id="1a916-169">Get Application ID</span></span>
* <span data-ttu-id="1a916-170">取得應用程式值</span><span class="sxs-lookup"><span data-stu-id="1a916-170">Get Application Value</span></span>
* <span data-ttu-id="1a916-171">取得通用識別碼</span><span class="sxs-lookup"><span data-stu-id="1a916-171">Get Common ID</span></span>
* <span data-ttu-id="1a916-172">取得通用值</span><span class="sxs-lookup"><span data-stu-id="1a916-172">Get Common Value</span></span>
* <span data-ttu-id="1a916-173">移除應用程式識別碼</span><span class="sxs-lookup"><span data-stu-id="1a916-173">Remove Application ID</span></span>
* <span data-ttu-id="1a916-174">設定通用識別碼</span><span class="sxs-lookup"><span data-stu-id="1a916-174">Set Common ID</span></span>
* <span data-ttu-id="1a916-175">值擷取程式</span><span class="sxs-lookup"><span data-stu-id="1a916-175">Value Extractor</span></span>

<span data-ttu-id="1a916-176">如需更多有關這些 functiods 的詳細資訊，請參閱**運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="1a916-176">For more details on these functiods, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>

## <a name="see-also"></a><span data-ttu-id="1a916-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a916-177">See Also</span></span>  
- [<span data-ttu-id="1a916-178">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="1a916-178">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
- <span data-ttu-id="1a916-179">**資料庫運算質參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="1a916-179">**Database Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
