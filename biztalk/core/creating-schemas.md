---
title: "建立結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 20b88194-b400-4ebc-8882-d493fbf30e0f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac019276923467fe2d95f5a0a0b4a7b53513e9c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-schemas"></a><span data-ttu-id="2d070-102">建立結構描述</span><span class="sxs-lookup"><span data-stu-id="2d070-102">Creating Schemas</span></span>
<span data-ttu-id="2d070-103">您可以使用 BizTalk 編輯器來建立兩種類型的結構描述： 訊息結構描述與屬性結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d070-103">You can use BizTalk Editor to create two types of schemas: message schemas and property schemas.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d070-104">訊息結構描述有數種類型，包括 XML 訊息結構描述、一般檔案訊息結構描述和信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d070-104">There are several types of message schemas, including XML message schemas, flat file message schemas, and envelope schemas.</span></span>  
  
 <span data-ttu-id="2d070-105">訊息結構描述會定義您預期要對您的交易夥伴或應用程式傳送及接收之訊息內容的結構與條件約束。</span><span class="sxs-lookup"><span data-stu-id="2d070-105">Message schemas define the structure and constrain the content of messages that you expect to send to, and receive from, your trading partners or applications.</span></span> <span data-ttu-id="2d070-106">訊息結構描述是最常見類型的結構描述，您將使用與 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2d070-106">Message schemas are the most common types of schemas that you will use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2d070-107">可以建立的商務文件和用來包含它們，信封的 XML 訊息結構描述，並透過使用 「 一般檔案延伸模組至 「 BizTalk 編輯器，它可以建立一般檔案訊息結構描述，包括標頭、 內文和結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d070-107"> can create XML message schemas for both business documents and the envelopes used to contain them, and through the use of the Flat File Extension to BizTalk Editor, it can create flat file message schemas, including schemas for headers, bodies and trailers.</span></span>  
  
 <span data-ttu-id="2d070-108">屬性結構描述為特殊類型的結構描述。</span><span class="sxs-lookup"><span data-stu-id="2d070-108">Property schemas are a special type of schema.</span></span> <span data-ttu-id="2d070-109">屬性結構描述會提供欄位和 (或) 記錄資料的驗證範本，在執行個體訊息中升級為所謂的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="2d070-109">Property schemas provide a validation template for field and/or record data that is promoted from within an instance message into what is known as the message context.</span></span> <span data-ttu-id="2d070-110">屬性結構描述的用途為提供正式的強型別資料定義，以便在執行階段升級。</span><span class="sxs-lookup"><span data-stu-id="2d070-110">The purpose of property schemas is to provide a formal, strongly typed definition of the data to be promoted at run time.</span></span>  
  
 <span data-ttu-id="2d070-111">屬性升級提供從執行個體訊息中提取主要資訊部分 (由您定義) 的集中機制，並使處理通過 BizTalk Server 之訊息的 BizTalk Server 元件更容易存取。</span><span class="sxs-lookup"><span data-stu-id="2d070-111">Property promotion provides a centralized mechanism for pulling key pieces of information, defined by you, from within an instance message and making it more easily accessible to BizTalk Server components that are handling the message as it passes through BizTalk Server.</span></span> <span data-ttu-id="2d070-112">升級屬性的最常用用途是比對訊息執行個體與訂閱，讓訊息可正確地傳遞以進行處理。</span><span class="sxs-lookup"><span data-stu-id="2d070-112">One common use of promoted properties is in matching a message instance to a subscription, allowing the message to be properly routed for processing.</span></span>  
  
 <span data-ttu-id="2d070-113">本節將描述在 BizTalk Server 中建立不同類型結構描述的方式，並呈現多種結構描述類型的相關主題。</span><span class="sxs-lookup"><span data-stu-id="2d070-113">This section describes the ways in which you can create different types of schemas within BizTalk Server, and presents related subjects that pertain to multiple types of schemas.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2d070-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="2d070-114">In This Section</span></span>  
  
-   [<span data-ttu-id="2d070-115">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="2d070-115">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)  
  
-   [<span data-ttu-id="2d070-116">管理結構描述中的節點</span><span class="sxs-lookup"><span data-stu-id="2d070-116">Managing the Nodes Within a Schema</span></span>](../core/managing-the-nodes-within-a-schema.md)  
  
-   [<span data-ttu-id="2d070-117">升級屬性</span><span class="sxs-lookup"><span data-stu-id="2d070-117">Promoting Properties</span></span>](../core/promoting-properties.md)