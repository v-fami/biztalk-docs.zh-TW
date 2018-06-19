---
title: 一般檔案訊息結尾 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cfe115a5-4fdc-4779-94f3-437b5a06fbd4
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cbeaef3f23de3cb89d873413964cd331ec23f43
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246286"
---
# <a name="flat-file-message-trailers"></a><span data-ttu-id="dfebd-102">一般檔案訊息結尾</span><span class="sxs-lookup"><span data-stu-id="dfebd-102">Flat File Message Trailers</span></span>
<span data-ttu-id="dfebd-103">與一般檔案執行個體訊息標頭，在一般檔案結構描述中設定所控制的選擇性一般檔案執行個體訊息結尾，一般檔案解譯器剖析**結尾結構描述**設計階段一般檔案解譯器的屬性或**XMLNORM。TrailerSpecName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="dfebd-103">As with flat file instance message headers, the parsing of the optional flat file instance message trailer by the flat file disassembler is controlled by the flat file schema that you have configured in the **Trailer schema** design-time property of the flat file disassembler or the **XMLNORM.TrailerSpecName** message context property.</span></span> <span data-ttu-id="dfebd-104">若您尚未使用兩個方法的其中一個來指定結構描述，則一般檔案解譯器會假設一般檔案執行個體訊息未包含結尾。</span><span class="sxs-lookup"><span data-stu-id="dfebd-104">If you have not specified a schema using one of these two methods, the flat file disassembler will assume that the flat file instance message does not contain a trailer.</span></span>  
  
 <span data-ttu-id="dfebd-105">不同於一般檔案執行個體訊息標頭，一般檔案執行個體訊息結尾無法以單一單位儲存和還原，也無法使用屬性升級將資料的個別項目複製到與一般檔案執行個體訊息內文關聯的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="dfebd-105">Unlike with flat file instance message headers, flat file instance message trailers can neither be saved and restored as a single unit, nor can they use property promotion to copy individual items of data to the message context associated with the flat file instance message body.</span></span> <span data-ttu-id="dfebd-106">不過，結尾可以加入輸出一般檔案執行個體訊息藉由指定適當的結構描述中**結尾結構描述**的一般檔案組合器的設計階段屬性或**XMLNORM。TrailerSpecName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="dfebd-106">However, a trailer can be added to an outbound flat file instance message by specifying the appropriate schema in the **Trailer schema** design-time property of the flat file assembler or the **XMLNORM.TrailerSpecName** message context property.</span></span> <span data-ttu-id="dfebd-107">構成結尾變動部分的資料，可以使用從一般檔案執行個體訊息內文的訊息內容之屬性降級來指定，或是在對應的結構描述中指定預設或固定值。</span><span class="sxs-lookup"><span data-stu-id="dfebd-107">The data that constitutes the variable portion of the trailer can be specified using property demotion from the message context of the flat file instance message body, or by specifying default or fixed values in the corresponding schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfebd-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dfebd-108">See Also</span></span>  
 <span data-ttu-id="dfebd-109">[一般檔案訊息標頭](../core/flat-file-message-headers.md) </span><span class="sxs-lookup"><span data-stu-id="dfebd-109">[Flat File Message Headers](../core/flat-file-message-headers.md) </span></span>  
 <span data-ttu-id="dfebd-110">[一般檔案訊息內文](../core/flat-file-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="dfebd-110">[Flat File Message Bodies](../core/flat-file-message-bodies.md) </span></span>  
 <span data-ttu-id="dfebd-111">[一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="dfebd-111">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 [<span data-ttu-id="dfebd-112">如何建立一般檔案訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="dfebd-112">How to Create Schemas for Flat File Messages</span></span>](../core/how-to-create-schemas-for-flat-file-messages.md)