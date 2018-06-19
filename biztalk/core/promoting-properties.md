---
title: 升級屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- properties, promoting
- promoting properties
- promoting properties, about promoting properties
ms.assetid: e1825028-7dd9-4eae-a383-4db12a83a402
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc1c5ac3e6e9aeadccc4eaefcb1457821ef36a93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22266422"
---
# <a name="promoting-properties"></a><span data-ttu-id="a385f-102">升級屬性</span><span class="sxs-lookup"><span data-stu-id="a385f-102">Promoting Properties</span></span>
<span data-ttu-id="a385f-103">升級屬性牽涉到將**欄位項目**或**欄位屬性**是結構描述中的節點**辨別欄位**或**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="a385f-103">Promotion of properties involves either promoting **Field Element** or **Field Attribute** nodes in a schema to be **Distinguished Fields** or **Property Fields**.</span></span> <span data-ttu-id="a385f-104">您也可以升級**記錄**節點做為**屬性欄位**有簡單內容 (**內容型別**屬性**記錄**節點設定為**SimpleContent**)。</span><span class="sxs-lookup"><span data-stu-id="a385f-104">You can also promote **Record** nodes as **Property Fields** if they have simple content (**Content Type** property of the **Record** node set to **SimpleContent**).</span></span> <span data-ttu-id="a385f-105">本節提供逐步指示，將節點升級為 **辨別欄位**或**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="a385f-105">This section provides step-by-step instructions for promoting nodes as either **Distinguished Fields** or as **Property Fields**.</span></span>  
  
 <span data-ttu-id="a385f-106">若要升級**記錄**（具有簡單內容）、**欄位項目**，或**欄位屬性**節點，做為**屬性欄位**，您可以先定義特殊類型的結構描述也稱為屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="a385f-106">To promote a **Record** (with simple content), **Field Element**, or **Field Attribute** node as a **Property Field**, you may first define a special type of schema called a property schema.</span></span> <span data-ttu-id="a385f-107">屬性結構描述定義的非結構化的集合**欄位項目**在您升級到其中的節點**記錄**（具有簡單內容）、**欄位項目**，或**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="a385f-107">Property schemas define an unstructured set of **Field Element** nodes into which you promote **Record** (with simple content), **Field Element**, or **Field Attribute** nodes.</span></span> <span data-ttu-id="a385f-108">建立屬性結構描述的逐步指示，請參閱[如何建立屬性結構描述](../core/how-to-create-property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="a385f-108">For step-by-step instructions for creating a property schema, see [How to Create Property Schemas](../core/how-to-create-property-schemas.md).</span></span>  
  
 <span data-ttu-id="a385f-109">或者，您可以使用**快速升級**功能，它會自動建立並更新單一屬性結構描述，只要當您升級新**欄位項目**，**欄位屬性**，或**記錄**（具有簡單內容） 節點。</span><span class="sxs-lookup"><span data-stu-id="a385f-109">Alternatively, you can use the **Quick Promotion** feature, which will automatically create and update a single property schema whenever you promote a new **Field Element**, **Field Attribute**, or **Record** (with simple content) node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a385f-110">您可以將欄位同時升級**辨別欄位**和**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="a385f-110">You can promote a field as both a **Distinguished Field** and a **Property Field**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a385f-111">**快速升級**功能插入具有升級的節點名稱的新屬性，藉以修改屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="a385f-111">The **Quick Promotion** feature modifies the property schema by inserting a new property with the name of the promoted node.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a385f-112">一旦您升級結構描述中的欄位之後，就不能將它移動或重新命名。</span><span class="sxs-lookup"><span data-stu-id="a385f-112">Do not move or rename a field in the schema once you have promoted it.</span></span> <span data-ttu-id="a385f-113">當您移動或重新命名結構描述欄位時，BizTalk 編輯器不會更新用來定義升級欄位位置的 XPath。</span><span class="sxs-lookup"><span data-stu-id="a385f-113">When you move or rename a schema field, BizTalk Editor does not update the XPath defining the location of the promoted field.</span></span>  
  
## <a name="xsd-and-clr-data-types"></a><span data-ttu-id="a385f-114">XSD 與 CLR 資料型別</span><span class="sxs-lookup"><span data-stu-id="a385f-114">XSD and CLR Data Types</span></span>  
 <span data-ttu-id="a385f-115">在某些地方，例如在屬性升級中，XSD 資料型別會升級為 Common Language Runtime (CLR) 資料型別。</span><span class="sxs-lookup"><span data-stu-id="a385f-115">In some places, such as in property promotion, XSD data types are promoted to Common Language Runtime (CLR) data types.</span></span> <span data-ttu-id="a385f-116">下表顯示可以升級的 XSD 資料型別以及對應的 CLR 資料型別。</span><span class="sxs-lookup"><span data-stu-id="a385f-116">The following table shows the XSD data types that can be promoted and the corresponding CLR data types.</span></span>  
  
|<span data-ttu-id="a385f-117">XSD 資料型別</span><span class="sxs-lookup"><span data-stu-id="a385f-117">XSD Data Type</span></span>|<span data-ttu-id="a385f-118">CLR 資料類型</span><span class="sxs-lookup"><span data-stu-id="a385f-118">CLR Data Type</span></span>|  
|-------------------|-------------------|  
|<span data-ttu-id="a385f-119">anyURI</span><span class="sxs-lookup"><span data-stu-id="a385f-119">anyURI</span></span>|<span data-ttu-id="a385f-120">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-120">String</span></span>|  
|<span data-ttu-id="a385f-121">布林</span><span class="sxs-lookup"><span data-stu-id="a385f-121">Boolean</span></span>|<span data-ttu-id="a385f-122">布林</span><span class="sxs-lookup"><span data-stu-id="a385f-122">Boolean</span></span>|  
|<span data-ttu-id="a385f-123">Byte</span><span class="sxs-lookup"><span data-stu-id="a385f-123">Byte</span></span>|<span data-ttu-id="a385f-124">sbyte</span><span class="sxs-lookup"><span data-stu-id="a385f-124">sbyte</span></span>|  
|<span data-ttu-id="a385f-125">日期</span><span class="sxs-lookup"><span data-stu-id="a385f-125">Date</span></span>|<span data-ttu-id="a385f-126">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-126">DateTime</span></span>|  
|<span data-ttu-id="a385f-127">dateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-127">dateTime</span></span>|<span data-ttu-id="a385f-128">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-128">DateTime</span></span>|  
|<span data-ttu-id="a385f-129">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-129">Decimal</span></span>|<span data-ttu-id="a385f-130">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-130">Decimal</span></span>|  
|<span data-ttu-id="a385f-131">Double</span><span class="sxs-lookup"><span data-stu-id="a385f-131">Double</span></span>|<span data-ttu-id="a385f-132">Double</span><span class="sxs-lookup"><span data-stu-id="a385f-132">Double</span></span>|  
|<span data-ttu-id="a385f-133">ENTITY</span><span class="sxs-lookup"><span data-stu-id="a385f-133">ENTITY</span></span>|<span data-ttu-id="a385f-134">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-134">String</span></span>|  
|<span data-ttu-id="a385f-135">Float</span><span class="sxs-lookup"><span data-stu-id="a385f-135">Float</span></span>|<span data-ttu-id="a385f-136">Single</span><span class="sxs-lookup"><span data-stu-id="a385f-136">Single</span></span>|  
|<span data-ttu-id="a385f-137">gDay</span><span class="sxs-lookup"><span data-stu-id="a385f-137">gDay</span></span>|<span data-ttu-id="a385f-138">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-138">DateTime</span></span>|  
|<span data-ttu-id="a385f-139">gMonth</span><span class="sxs-lookup"><span data-stu-id="a385f-139">gMonth</span></span>|<span data-ttu-id="a385f-140">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-140">DateTime</span></span>|  
|<span data-ttu-id="a385f-141">gMonthDay</span><span class="sxs-lookup"><span data-stu-id="a385f-141">gMonthDay</span></span>|<span data-ttu-id="a385f-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-142">DateTime</span></span>|  
|<span data-ttu-id="a385f-143">gYear</span><span class="sxs-lookup"><span data-stu-id="a385f-143">gYear</span></span>|<span data-ttu-id="a385f-144">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-144">DateTime</span></span>|  
|<span data-ttu-id="a385f-145">gYearMonth</span><span class="sxs-lookup"><span data-stu-id="a385f-145">gYearMonth</span></span>|<span data-ttu-id="a385f-146">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-146">DateTime</span></span>|  
|<span data-ttu-id="a385f-147">ID</span><span class="sxs-lookup"><span data-stu-id="a385f-147">ID</span></span>|<span data-ttu-id="a385f-148">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-148">String</span></span>|  
|<span data-ttu-id="a385f-149">IDREF</span><span class="sxs-lookup"><span data-stu-id="a385f-149">IDREF</span></span>|<span data-ttu-id="a385f-150">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-150">String</span></span>|  
|<span data-ttu-id="a385f-151">int</span><span class="sxs-lookup"><span data-stu-id="a385f-151">Int</span></span>|<span data-ttu-id="a385f-152">Int32</span><span class="sxs-lookup"><span data-stu-id="a385f-152">Int32</span></span>|  
|<span data-ttu-id="a385f-153">Integer</span><span class="sxs-lookup"><span data-stu-id="a385f-153">Integer</span></span>|<span data-ttu-id="a385f-154">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-154">Decimal</span></span>|  
|<span data-ttu-id="a385f-155">語言</span><span class="sxs-lookup"><span data-stu-id="a385f-155">Language</span></span>|<span data-ttu-id="a385f-156">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-156">String</span></span>|  
|<span data-ttu-id="a385f-157">名稱</span><span class="sxs-lookup"><span data-stu-id="a385f-157">Name</span></span>|<span data-ttu-id="a385f-158">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-158">String</span></span>|  
|<span data-ttu-id="a385f-159">NCName</span><span class="sxs-lookup"><span data-stu-id="a385f-159">NCName</span></span>|<span data-ttu-id="a385f-160">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-160">String</span></span>|  
|<span data-ttu-id="a385f-161">negativeInteger</span><span class="sxs-lookup"><span data-stu-id="a385f-161">negativeInteger</span></span>|<span data-ttu-id="a385f-162">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-162">Decimal</span></span>|  
|<span data-ttu-id="a385f-163">NMTOKEN</span><span class="sxs-lookup"><span data-stu-id="a385f-163">NMTOKEN</span></span>|<span data-ttu-id="a385f-164">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-164">String</span></span>|  
|<span data-ttu-id="a385f-165">nonNegativeInteger</span><span class="sxs-lookup"><span data-stu-id="a385f-165">nonNegativeInteger</span></span>|<span data-ttu-id="a385f-166">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-166">Decimal</span></span>|  
|<span data-ttu-id="a385f-167">nonPositiveInteger</span><span class="sxs-lookup"><span data-stu-id="a385f-167">nonPositiveInteger</span></span>|<span data-ttu-id="a385f-168">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-168">Decimal</span></span>|  
|<span data-ttu-id="a385f-169">normalizedString</span><span class="sxs-lookup"><span data-stu-id="a385f-169">normalizedString</span></span>|<span data-ttu-id="a385f-170">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-170">String</span></span>|  
|<span data-ttu-id="a385f-171">NOTATION</span><span class="sxs-lookup"><span data-stu-id="a385f-171">NOTATION</span></span>|<span data-ttu-id="a385f-172">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-172">String</span></span>|  
|<span data-ttu-id="a385f-173">positiveInteger</span><span class="sxs-lookup"><span data-stu-id="a385f-173">positiveInteger</span></span>|<span data-ttu-id="a385f-174">Decimal</span><span class="sxs-lookup"><span data-stu-id="a385f-174">Decimal</span></span>|  
|<span data-ttu-id="a385f-175">QName</span><span class="sxs-lookup"><span data-stu-id="a385f-175">QName</span></span>|<span data-ttu-id="a385f-176">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-176">String</span></span>|  
|<span data-ttu-id="a385f-177">Short</span><span class="sxs-lookup"><span data-stu-id="a385f-177">Short</span></span>|<span data-ttu-id="a385f-178">Int16</span><span class="sxs-lookup"><span data-stu-id="a385f-178">Int16</span></span>|  
|<span data-ttu-id="a385f-179">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-179">String</span></span>|<span data-ttu-id="a385f-180">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-180">String</span></span>|  
|<span data-ttu-id="a385f-181">Time</span><span class="sxs-lookup"><span data-stu-id="a385f-181">Time</span></span>|<span data-ttu-id="a385f-182">DateTime</span><span class="sxs-lookup"><span data-stu-id="a385f-182">DateTime</span></span>|  
|<span data-ttu-id="a385f-183">Token</span><span class="sxs-lookup"><span data-stu-id="a385f-183">Token</span></span>|<span data-ttu-id="a385f-184">字串</span><span class="sxs-lookup"><span data-stu-id="a385f-184">String</span></span>|  
|<span data-ttu-id="a385f-185">unsignedByte</span><span class="sxs-lookup"><span data-stu-id="a385f-185">unsignedByte</span></span>|<span data-ttu-id="a385f-186">Byte</span><span class="sxs-lookup"><span data-stu-id="a385f-186">Byte</span></span>|  
|<span data-ttu-id="a385f-187">unsignedInt</span><span class="sxs-lookup"><span data-stu-id="a385f-187">unsignedInt</span></span>|<span data-ttu-id="a385f-188">UInt32</span><span class="sxs-lookup"><span data-stu-id="a385f-188">UInt32</span></span>|  
|<span data-ttu-id="a385f-189">unsignedShort</span><span class="sxs-lookup"><span data-stu-id="a385f-189">unsignedShort</span></span>|<span data-ttu-id="a385f-190">UInt16</span><span class="sxs-lookup"><span data-stu-id="a385f-190">UInt16</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a385f-191">XSD 的資料型別 base64Binary、duration、ENTITES、hexBinary、IDREFS、long、NMTOKENS 和 unsignedLong 不支援升級。</span><span class="sxs-lookup"><span data-stu-id="a385f-191">XSD Data Type of base64Binary, duration, ENTITES, hexBinary, IDREFS, long, NMTOKENS, and unsignedLong are not supported for promotion.</span></span>  
  
## <a name="limitations-for-promoting-properties"></a><span data-ttu-id="a385f-192">升級屬性的限制</span><span class="sxs-lookup"><span data-stu-id="a385f-192">Limitations for Promoting Properties</span></span>  
 <span data-ttu-id="a385f-193">在升級屬性時請考量下列事項：</span><span class="sxs-lookup"><span data-stu-id="a385f-193">When promoting properties, consider the following:</span></span>  
  
-   <span data-ttu-id="a385f-194">升級屬性的長度有 256 個字元的限制，但是寫入屬性並無長度限制。</span><span class="sxs-lookup"><span data-stu-id="a385f-194">Promoted properties are limited to 256 characters in length while written properties have no length limitation.</span></span>  
  
-   <span data-ttu-id="a385f-195">升級屬性是用於訊息路由中，且基於比較與儲存效率的原因，所以在大小上會有所限制。</span><span class="sxs-lookup"><span data-stu-id="a385f-195">Promoted properties are used in message routing and are limited in size for reasons of efficiency in comparison and storage.</span></span> <span data-ttu-id="a385f-196">雖然寫入屬性在大小上並無嚴格限制，在內容中使用過大的值會影響效能，因為這些值仍會被處理並與訊息一起傳遞。</span><span class="sxs-lookup"><span data-stu-id="a385f-196">While written properties have no hard limits on size, using excessively large values in the context will have an impact on performance, because those values must still be processed and passed with the message.</span></span> <span data-ttu-id="a385f-197">[辨別欄位] 即為寫入屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="a385f-197">Distinguished Fields are the examples of written properties.</span></span>  
  
-   <span data-ttu-id="a385f-198">記錄節點永遠不會升級為**辨別欄位**。</span><span class="sxs-lookup"><span data-stu-id="a385f-198">Record nodes can never be promoted as **Distinguished Fields**.</span></span>  
  
-   <span data-ttu-id="a385f-199">升級屬性僅限非重複項目/屬性。</span><span class="sxs-lookup"><span data-stu-id="a385f-199">Promoted properties are restricted to non-repeating elements/attributes.</span></span>  
  
-   <span data-ttu-id="a385f-200">請勿將屬於相同根節點的欄位升級至相同的屬性。</span><span class="sxs-lookup"><span data-stu-id="a385f-200">Do not promote fields belonging to the same root node to the same property.</span></span> <span data-ttu-id="a385f-201">這類升級會產生編譯或部署錯誤。</span><span class="sxs-lookup"><span data-stu-id="a385f-201">Such promotions produce compilation or deployment errors.</span></span>  
  
-   <span data-ttu-id="a385f-202">在訊息內容中無法使用部分屬性，這是因為這些屬性尚未升級。</span><span class="sxs-lookup"><span data-stu-id="a385f-202">Within a message context, there are some properties that are not available since they are not promoted.</span></span>  <span data-ttu-id="a385f-203">BTS.ReceiveLocationName 屬性即為其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="a385f-203">The BTS.ReceiveLocationName property is one such property.</span></span> <span data-ttu-id="a385f-204">如果您可以將新的屬性結構描述或新的 BizTalk Server 專案加到開發中，就有辦法從協調流程中存取這個屬性。</span><span class="sxs-lookup"><span data-stu-id="a385f-204">If you can add a new property schema or a new BizTalk Server project to your development it is possible to access this property from within an orchestration.</span></span>  
  
     <span data-ttu-id="a385f-205">屬性值是以屬性目標命名空間和屬性名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="a385f-205">Property values are identified by the property target namespace and property name.</span></span>  <span data-ttu-id="a385f-206">下列範例顯示如何以程式碼存取接收位置。</span><span class="sxs-lookup"><span data-stu-id="a385f-206">The following example shows how to access the receive location in code.</span></span>  
  
     `string receiveLocationName =       pInMsg.Context.Read("ReceiveLocationName", sysNamespace);`  
  
## <a name="in-this-section"></a><span data-ttu-id="a385f-207">本節內容</span><span class="sxs-lookup"><span data-stu-id="a385f-207">In This Section</span></span>  
  
-   [<span data-ttu-id="a385f-208">如何開啟升級屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="a385f-208">How to Open the Promote Properties Dialog Box</span></span>](../core/how-to-open-the-promote-properties-dialog-box.md)  
  
-   [<span data-ttu-id="a385f-209">如何將資料複製到訊息內容做為辨別欄位</span><span class="sxs-lookup"><span data-stu-id="a385f-209">How to Copy Data to the Message Context as Distinguished Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-distinguished-fields.md)  
  
-   [<span data-ttu-id="a385f-210">如何將資料複製到訊息內容做為屬性欄位</span><span class="sxs-lookup"><span data-stu-id="a385f-210">How to Copy Data to the Message Context as Property Fields</span></span>](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)