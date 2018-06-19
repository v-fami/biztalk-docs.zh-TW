---
title: 一般檔案訊息標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1981daaf-149a-426d-9a2f-5fcf64bce185
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 271e9fe74d0a55f4b3ff5271861d24474fffaf37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246350"
---
# <a name="flat-file-message-headers"></a><span data-ttu-id="79546-102">一般檔案訊息標頭</span><span class="sxs-lookup"><span data-stu-id="79546-102">Flat File Message Headers</span></span>
<span data-ttu-id="79546-103">選擇性的一般檔案執行個體訊息標頭，一般檔案解譯器剖析由您在設定一般檔案結構描述**標頭結構描述**的一般檔案解譯器的設計階段屬性或**XMLNORM。HeaderSpecName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="79546-103">The parsing of the optional flat file instance message header by the flat file disassembler is controlled by the flat file schema that you have configured in the **Header schema** design-time property of the flat file disassembler or the **XMLNORM.HeaderSpecName** message context property.</span></span> <span data-ttu-id="79546-104">若您並未使用這兩種方法的其中一種來指定結構描述，則一般檔案解譯器就會假設一般檔案執行個體訊息沒有包含標頭。</span><span class="sxs-lookup"><span data-stu-id="79546-104">If you have not specified a schema using one of these two methods, the flat file disassembler assumes that the flat file instance message does not contain a header.</span></span>  

## <a name="outbound-messages"></a><span data-ttu-id="79546-105">輸出訊息</span><span class="sxs-lookup"><span data-stu-id="79546-105">Outbound messages</span></span>  
 <span data-ttu-id="79546-106">對於輸出一般檔案執行個體訊息，您可以設定要產生標頭指定適當的結構描述中的一般檔案組合器其**標頭規格名稱**設計階段屬性或**XMLNORM。HeaderSpecName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="79546-106">For outbound flat file instance messages, you can configure the flat file assembler to produce a header by specifying the appropriate schema in its **Header Specification Name** design-time property or the **XMLNORM.HeaderSpecName** message context property.</span></span> <span data-ttu-id="79546-107">如需有關如何設定訊息內容屬性的詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="79546-107">For more information about setting message context properties, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  

## <a name="inbound-messages"></a><span data-ttu-id="79546-108">輸入的訊息</span><span class="sxs-lookup"><span data-stu-id="79546-108">Inbound messages</span></span>  
 <span data-ttu-id="79546-109">輸入一般檔案執行個體訊息標頭中所找到的資料，可以透過兩種不同的方式加以保存和利用。</span><span class="sxs-lookup"><span data-stu-id="79546-109">Data found in inbound flat file instance message headers can be preserved and utilized in two different ways.</span></span> <span data-ttu-id="79546-110">第一個方法是，一般檔案執行個體訊息標頭可以完整地儲存於內文的訊息內容裡，以便日後還原時，做為對應輸出一般檔案執行個體訊息的標頭。</span><span class="sxs-lookup"><span data-stu-id="79546-110">First, flat file instance message headers can be saved in their entirety within the message context of the body for later restoration as the header of a corresponding outbound flat file instance message.</span></span> <span data-ttu-id="79546-111">您可以使用**保留標頭**屬性來指定，應該保留標頭的接收管線。</span><span class="sxs-lookup"><span data-stu-id="79546-111">You can use the **Preserve header** property of the receive pipeline to specify that the header should be preserved.</span></span> <span data-ttu-id="79546-112">此外，若一般檔案組合器中指定了標頭，則輸出訊息上便會使用保留的標頭。</span><span class="sxs-lookup"><span data-stu-id="79546-112">And if a header is specified in the flat file assembler, the preserved header will be used on the outbound message.</span></span>  
  
 <span data-ttu-id="79546-113">第二個方法是，一般檔案執行個體訊息中的個別資料項目，可以藉由指定對應結構描述中一或多個欄位的屬性升級，複製到與一般檔案訊息內文相關聯的訊息內容中。</span><span class="sxs-lookup"><span data-stu-id="79546-113">Second, individual items of data from a flat file instance message header can be copied to the message context associated with the flat file message body by specifying property promotion for one or more of the fields in the corresponding schema.</span></span> <span data-ttu-id="79546-114">如需有關如何升級屬性的詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="79546-114">For more information about promoting properties, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79546-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79546-115">See Also</span></span>  
 <span data-ttu-id="79546-116">[一般檔案訊息內文](../core/flat-file-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="79546-116">[Flat File Message Bodies](../core/flat-file-message-bodies.md) </span></span>  
 <span data-ttu-id="79546-117">[一般檔案訊息結尾](../core/flat-file-message-trailers.md) </span><span class="sxs-lookup"><span data-stu-id="79546-117">[Flat File Message Trailers](../core/flat-file-message-trailers.md) </span></span>  
 <span data-ttu-id="79546-118">[一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="79546-118">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 [<span data-ttu-id="79546-119">如何建立一般檔案訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="79546-119">How to Create Schemas for Flat File Messages</span></span>](../core/how-to-create-schemas-for-flat-file-messages.md)