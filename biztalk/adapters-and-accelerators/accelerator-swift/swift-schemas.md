---
title: SWIFT 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT, SWIFT messages
- schemas, SWIFT
- SWIFT messages, SWIFT schemas
- SWIFT, schemas
ms.assetid: 53017a56-a718-4577-a08c-9c92d9a54e7a
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f749a06c694007008f3d8138b2b087b77b2c4f03
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996111"
---
# <a name="swift-schemas"></a><span data-ttu-id="872b7-102">SWIFT 結構描述</span><span class="sxs-lookup"><span data-stu-id="872b7-102">SWIFT Schemas</span></span>
[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]<span data-ttu-id="872b7-103"> 傳送和接收 SWIFT 財務 (FIN) 訊息以個別的一般檔案的 SWIFT 網路移轉。</span><span class="sxs-lookup"><span data-stu-id="872b7-103"> sends and receives SWIFT financial (FIN) messages as individual flat files over the SWIFT network.</span></span> <span data-ttu-id="872b7-104">每個個別的訊息是由一組的標頭區塊的一組預先定義的加上標籤的欄位和位置，或已排序的子欄位，並在結尾區塊的結尾的一組所組成的文字區塊所組成。</span><span class="sxs-lookup"><span data-stu-id="872b7-104">Each individual message consists of a set of header blocks, a text block made up of a predefined set of labeled fields and positional or ordered subfields, and a set of trailers inside a trailer block.</span></span> <span data-ttu-id="872b7-105">文字區塊的內容是根據訊息類型而異。</span><span class="sxs-lookup"><span data-stu-id="872b7-105">The content of the text block varies by message type.</span></span>  
  
 <span data-ttu-id="872b7-106">另外還有許多應用程式，交換的 SWIFT 的財務 (FIN) 訊息的批次-一組包含單一檔案中的訊息。</span><span class="sxs-lookup"><span data-stu-id="872b7-106">There are also many applications, which exchange batches of SWIFT financial (FIN) messages—a set of messages contained in a single file.</span></span> <span data-ttu-id="872b7-107">檔案可能會在本機傳遞，或可能透過 FileAct 傳輸 (透過 SWIFT IP 網路 — SIPN)，或透過 FTP。</span><span class="sxs-lookup"><span data-stu-id="872b7-107">The file may be delivered locally or may be transmitted through FileAct (over the SWIFT IP Network—SIPN), or through FTP.</span></span>  
  
 <span data-ttu-id="872b7-108">若要簡化資料的操作相關聯這些訊息，不論它們是在批次還是個別提交 Microsoft[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]提供 XSD 結構描述中定義每個訊息類型。</span><span class="sxs-lookup"><span data-stu-id="872b7-108">To simplify the manipulation of the data associated with these messages, regardless of whether they are batched or submitted individually, Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)] provides an XSD schema defining each message type.</span></span> <span data-ttu-id="872b7-109">此結構描述，讓訊息可以自動與適當的結構描述，產生關聯，並自動轉換與 XML 的 SWIFT 網路所使用的外部的一般檔案表示法之間，會升級訊息類型。</span><span class="sxs-lookup"><span data-stu-id="872b7-109">This schema promotes the message type so that messages can be automatically associated with the proper schema, and automatically transformed between the external flat file representation, used by the SWIFT network, to and from XML.</span></span>  
  
 <span data-ttu-id="872b7-110">結構描述包含的所有區塊，包括標頭、 文字和結尾。</span><span class="sxs-lookup"><span data-stu-id="872b7-110">The schema includes all of the blocks including headers, text, and trailers.</span></span> <span data-ttu-id="872b7-111">此結構描述，交換結構描述，因為它是完整透過使用 FIN 訊息層級通訊協定的 SWIFT 網路來傳送訊息，並包含所有透過 SWIFT 網路接收之訊息相關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="872b7-111">This schema is an interchange schema, because it is comprehensive enough to transmit messages over the SWIFT network using the FIN message-level protocols, and to contain all of the information associated with a message received through the SWIFT network.</span></span>  
  
 <span data-ttu-id="872b7-112">每個訊息類型的結構描述會定義整體的格式和內容，該訊息類型。</span><span class="sxs-lookup"><span data-stu-id="872b7-112">The schema for each message type defines the overall format and context of that message type.</span></span> <span data-ttu-id="872b7-113">A4SWIFT 定義每個區塊。</span><span class="sxs-lookup"><span data-stu-id="872b7-113">A4SWIFT defines each block.</span></span> <span data-ttu-id="872b7-114">每個區塊中，欄位和子配置。視需要的欄位和子欄位所建置的通用基底或複雜類型，在不同的結構描述中定義。</span><span class="sxs-lookup"><span data-stu-id="872b7-114">Inside each block, the fields and subfields are laid out. As appropriate, the fields and subfields are built from common base or complex types, defined in separate schemas.</span></span> <span data-ttu-id="872b7-115">結構描述層級的驗證包括格式、 字元集，設定值、 範圍、 必要/選用，重複性、 位置和長度，視需要。</span><span class="sxs-lookup"><span data-stu-id="872b7-115">Schema-level validation includes format, character set, value set, range, required/optional, repeatability, position, and length, as appropriate.</span></span> <span data-ttu-id="872b7-116">商務規則執行跨欄位驗證和其他邏輯檢查。</span><span class="sxs-lookup"><span data-stu-id="872b7-116">The business rules perform cross-field validations and other logical checks.</span></span>  
  
 <span data-ttu-id="872b7-117">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="872b7-117">This section contains:</span></span>  
  
-   [<span data-ttu-id="872b7-118">範例訊息呈現</span><span class="sxs-lookup"><span data-stu-id="872b7-118">Sample Message Presentation</span></span>](../../adapters-and-accelerators/accelerator-swift/sample-message-presentation.md)  
  
-   [<span data-ttu-id="872b7-119">範例結構描述呈現</span><span class="sxs-lookup"><span data-stu-id="872b7-119">Sample Schema Presentation</span></span>](../../adapters-and-accelerators/accelerator-swift/sample-schema-presentation.md)  
  
-   [<span data-ttu-id="872b7-120">SWIFT 標頭</span><span class="sxs-lookup"><span data-stu-id="872b7-120">SWIFT Headers</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-headers.md)  
  
-   [<span data-ttu-id="872b7-121">SWIFT 文字</span><span class="sxs-lookup"><span data-stu-id="872b7-121">SWIFT Text</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-text.md)  
  
-   [<span data-ttu-id="872b7-122">SWIFT 結尾</span><span class="sxs-lookup"><span data-stu-id="872b7-122">SWIFT Trailers</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-trailers.md)  
  
-   [<span data-ttu-id="872b7-123">更新 SWIFT 訊息標準</span><span class="sxs-lookup"><span data-stu-id="872b7-123">Updating SWIFT Message Standards</span></span>](../../adapters-and-accelerators/accelerator-swift/updating-swift-messaging-standards.md)