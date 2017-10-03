---
title: "如何使用訊息內容控制訊息處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1e3792e-9cd4-42b6-8b9d-3c2a022a16d6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73d356496d07bb2227aa514ee68f2a2a51e2291b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-message-content-to-control-message-processing"></a><span data-ttu-id="975a0-102">使用訊息內容控制訊息處理的方式</span><span class="sxs-lookup"><span data-stu-id="975a0-102">Ways to Use Message Content to Control Message Processing</span></span>
<span data-ttu-id="975a0-103">有兩種類型的屬性升級：**辨別欄位**和**屬性欄位**，後者使用屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="975a0-103">There are two types of property promotion: **Distinguished Fields** and **Property Fields**, the latter of which uses property schemas.</span></span> <span data-ttu-id="975a0-104">在 [BizTalk 編輯器] 中，您管理這兩種類型的屬性升級使用**升級屬性**對話方塊中，以存取使用**升級屬性**屬性**結構描述**節點。</span><span class="sxs-lookup"><span data-stu-id="975a0-104">In BizTalk Editor, you manage both of these types of property promotion by using the **Promote Properties** dialog box, which is accessible by using the **Promote Properties** property of the **Schema** node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="975a0-105">您可升級的值有部分限制。</span><span class="sxs-lookup"><span data-stu-id="975a0-105">There are some restrictions on values that you can promote.</span></span> <span data-ttu-id="975a0-106">如需詳細資訊，請參閱中的資料表[升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="975a0-106">For more information, see the table in [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
 <span data-ttu-id="975a0-107">您必須根據實例的詳細資料來決定要使用的屬性升級類型。</span><span class="sxs-lookup"><span data-stu-id="975a0-107">You must decide which type of property promotion to use based on the details of your scenario.</span></span> <span data-ttu-id="975a0-108">請考慮下列差異**辨別欄位**屬性升級和**屬性欄位**屬性升級：</span><span class="sxs-lookup"><span data-stu-id="975a0-108">Consider the following distinctions between **Distinguished Field** property promotion and **Property Field** property promotion:</span></span>  
  
-   <span data-ttu-id="975a0-109">**辨別欄位**不能參與訊息路由，因此它們沒有出現在篩選運算式中。</span><span class="sxs-lookup"><span data-stu-id="975a0-109">**Distinguished Fields** cannot participate in message routing and therefore they do not appear in the filter expressions.</span></span> <span data-ttu-id="975a0-110">它們只有在協調流程的內容中可以使用，不過，它們在傳送和接收訊息時的負擔較小。</span><span class="sxs-lookup"><span data-stu-id="975a0-110">They are only available within the context of an orchestration but they have less overhead when sending and receiving messages.</span></span>  
  
-   <span data-ttu-id="975a0-111">**辨別欄位**並沒有任何大小限制。</span><span class="sxs-lookup"><span data-stu-id="975a0-111">**Distinguished Fields** do not have any size limitations.</span></span> <span data-ttu-id="975a0-112">**屬性欄位**限制為 255 個字元。</span><span class="sxs-lookup"><span data-stu-id="975a0-112">**Property Fields** are limited to 255 characters.</span></span>  
  
-   <span data-ttu-id="975a0-113">**辨別欄位**不需要任何獨立的成品可以建立，但是**屬性欄位**需要建立和維護屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="975a0-113">**Distinguished Fields** do not require any separate artifacts to be created whereas **Property Fields** require the creation and maintenance of a property schema.</span></span>  
  
 <span data-ttu-id="975a0-114">根據這些考量，您應該將節點升級為**屬性欄位**只有當您想要使用的升級的屬性輸入路由或追蹤的訊息。</span><span class="sxs-lookup"><span data-stu-id="975a0-114">Drawing upon these considerations, you should promote nodes as **Property Fields** only when you intend to use the promoted properties for message routing or tracking purposes.</span></span> <span data-ttu-id="975a0-115">否則，如果您只存取協調流程中的升級的屬性，您應該利用事實的**辨別欄位**是成本更低、 較輕量級，但更容易使用比**屬性欄位**。</span><span class="sxs-lookup"><span data-stu-id="975a0-115">Otherwise, if you are only going to access the promoted properties from within your orchestrations, you should take advantage of the fact that **Distinguished Fields** are much cheaper, more lightweight, and more easy-to-use than **Property Fields**.</span></span>  
  
 <span data-ttu-id="975a0-116">使用升級屬性**辨別欄位**機制只是從協調流程中存取，而且不能從管線、 連接埠，以及其他存取。</span><span class="sxs-lookup"><span data-stu-id="975a0-116">Properties promoted by using the **Distinguished Field** mechanism are only accessible from within orchestrations and cannot be accessed from pipelines, ports, and so on.</span></span> <span data-ttu-id="975a0-117">相反地，使用升級屬性**屬性欄位**，屬性結構描述機制可從所有這些元件。</span><span class="sxs-lookup"><span data-stu-id="975a0-117">On the other hand, properties promoted by using the **Property Fields** and property schema mechanism are accessible from all of these components.</span></span> <span data-ttu-id="975a0-118">另一個重要的差異是屬性欄位值的限制為 255 個字元，但是辨別欄位值則沒有這類限制。</span><span class="sxs-lookup"><span data-stu-id="975a0-118">Another important difference is that property field values are limited to 255 characters and distinguished field values have no such limit.</span></span>  
  
 <span data-ttu-id="975a0-119">本節提供兩種類型的屬性升級相關資訊，包括如何使用 BizTalk 編輯器為訊息結構描述建立這類升級屬性的解說資訊。</span><span class="sxs-lookup"><span data-stu-id="975a0-119">This section provides information about these two types of property promotion, including how information about how to establish such promoted properties for a message schema by using BizTalk Editor.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="975a0-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="975a0-120">In This Section</span></span>  
  
-   [<span data-ttu-id="975a0-121">關於 BizTalk 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="975a0-121">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)  
  
-   [<span data-ttu-id="975a0-122">執行個體訊息使用辨別欄位處理</span><span class="sxs-lookup"><span data-stu-id="975a0-122">Instance Message Processing Using Distinguished Fields</span></span>](../core/instance-message-processing-using-distinguished-fields.md)  
  
-   [<span data-ttu-id="975a0-123">使用屬性升級處理執行個體訊息</span><span class="sxs-lookup"><span data-stu-id="975a0-123">Instance Message Processing Using Property Promotion</span></span>](../core/instance-message-processing-using-property-promotion.md)