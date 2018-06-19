---
title: 一般檔案訊息內文 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 097e49a1-75d2-44a4-9372-d78de7b7597c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2de8748d9a36c817f7db8fed96a59c8d2bd7dda2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246782"
---
# <a name="flat-file-message-bodies"></a><span data-ttu-id="42322-102">一般檔案訊息內文</span><span class="sxs-lookup"><span data-stu-id="42322-102">Flat File Message Bodies</span></span>
<span data-ttu-id="42322-103">一般檔案執行個體訊息內文為必要項目，一般檔案解譯器會將其處理為一或多個 XML 執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="42322-103">A flat file instance message body, which is required, is what the flat file disassembler processes into one or more XML instance messages.</span></span> <span data-ttu-id="42322-104">若要知道在內送一般檔案執行個體訊息內文中有哪些資料，您必須使用與內文對應的一般檔案結構描述來設定一般檔案解譯器。</span><span class="sxs-lookup"><span data-stu-id="42322-104">To know what data to expect in an inbound flat file instance message body, you must configure the flat file disassembler with the flat file schema that corresponds to the body.</span></span> <span data-ttu-id="42322-105">您可以使用指定的結構描述**文件結構描述**的一般檔案解譯器的設計階段屬性或**XMLNORM。DocumentSpecName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="42322-105">You can specify the schema by using the **Document schema** design-time property of the flat file disassembler or the **XMLNORM.DocumentSpecName** message context property.</span></span> <span data-ttu-id="42322-106">因為一般檔案執行個體訊息必須要有內文部分，所以，您必須使用這兩個方法其中一個來設定適當的結構描述。</span><span class="sxs-lookup"><span data-stu-id="42322-106">Because flat file instance messages must have a body part, you must configure the appropriate schema using one of these two methods.</span></span>  
  
 <span data-ttu-id="42322-107">如為輸出一般檔案執行個體訊息，一般檔案組合器可以為執行個體訊息的內文動態決定適當的一般檔案結構描述。</span><span class="sxs-lookup"><span data-stu-id="42322-107">For outbound flat file instance messages, the flat file assembler can dynamically determine the appropriate flat file schema for the body of the instance message.</span></span> <span data-ttu-id="42322-108">一般檔案組合器會從訊息類型決定適當的結構描述，它是目標命名空間與根項目名稱兩者的組合，而這兩者都必須存在於輸出訊息的 XML 版本中。</span><span class="sxs-lookup"><span data-stu-id="42322-108">The flat file assembler determines the appropriate schema from the message type, which is a combination of the target namespace and the name of the root element, both of which must be present in the XML version of the outbound message.</span></span> <span data-ttu-id="42322-109">或者，您可以明確地設定可供設定的一般檔案結構描述**文件結構描述**的一般檔案組合器的設計階段屬性或**XMLNORM。DocumentSpecName**訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="42322-109">Alternatively, you can explicitly configure the flat file schema to be used by configuring the **Document schema** design-time property of the flat file assembler or the **XMLNORM.DocumentSpecName** message context property.</span></span>  
  
 <span data-ttu-id="42322-110">透過指定一般檔案解譯器所使用之一般檔案結構描述中的屬性升級，來處理輸入執行個體訊息，就可以將在輸入一般檔案執行個體訊息內文中找到的資料複製到對應的訊息內容。</span><span class="sxs-lookup"><span data-stu-id="42322-110">Data found in inbound flat file instance message bodies can be copied to the corresponding message context by specifying property promotion in the flat file schema being used by the flat file disassembler to process the inbound instance message.</span></span> <span data-ttu-id="42322-111">同樣地，透過指定一般檔案組合器所使用之一般檔案結構描述中的屬性降級，來處理輸出訊息，就可以將訊息內容中的資料複製回輸出一般檔案執行個體訊息中。</span><span class="sxs-lookup"><span data-stu-id="42322-111">Likewise, data in the message context can be copied back into outbound flat file instance messages by specifying property demotion in the flat file schema being used by the flat file assembler to process the outbound message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42322-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42322-112">See Also</span></span>  
 <span data-ttu-id="42322-113">[一般檔案訊息標頭](../core/flat-file-message-headers.md) </span><span class="sxs-lookup"><span data-stu-id="42322-113">[Flat File Message Headers](../core/flat-file-message-headers.md) </span></span>  
 <span data-ttu-id="42322-114">[一般檔案訊息結尾](../core/flat-file-message-trailers.md) </span><span class="sxs-lookup"><span data-stu-id="42322-114">[Flat File Message Trailers](../core/flat-file-message-trailers.md) </span></span>  
 <span data-ttu-id="42322-115">[一般檔案訊息的結構](../core/structure-of-a-flat-file-message.md) </span><span class="sxs-lookup"><span data-stu-id="42322-115">[Structure of a Flat File Message](../core/structure-of-a-flat-file-message.md) </span></span>  
 [<span data-ttu-id="42322-116">如何建立一般檔案訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="42322-116">How to Create Schemas for Flat File Messages</span></span>](../core/how-to-create-schemas-for-flat-file-messages.md)