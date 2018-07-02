---
title: 使用結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developing, schemas
- schemas, developing
ms.assetid: 123c4b43-34e4-41c7-980d-5d518b1479c1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb6ac17cd0959d712da290b937a961d517f320e7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968359"
---
# <a name="working-with-schemas"></a><span data-ttu-id="d62e7-102">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="d62e7-102">Working with Schemas</span></span>
<span data-ttu-id="d62e7-103">在 Microsoft 所提供的結構描述[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是全球 Interbank 財務電信 (SWIFT) FIN 訊息協會 Microsoft XSD 表示法。</span><span class="sxs-lookup"><span data-stu-id="d62e7-103">The schemas provided in Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are the Microsoft XSD representation of the Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages.</span></span> <span data-ttu-id="d62e7-104">每個訊息類型都有自己的結構描述，包括 SWIFT 標頭和 SWIFT trailer （交換格式）。</span><span class="sxs-lookup"><span data-stu-id="d62e7-104">Each message type has its own schema, including the SWIFT header and SWIFT trailer (interchange format).</span></span> <span data-ttu-id="d62e7-105">此結構描述是不足，無法傳送或接收 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="d62e7-105">This schema is sufficient to send or receive a SWIFT message.</span></span> <span data-ttu-id="d62e7-106">這些結構描述是唯一的分隔和位置記錄，以提供詳細的 XML 表示法，一般檔案 FIN 結構的混合。</span><span class="sxs-lookup"><span data-stu-id="d62e7-106">These schemas are a unique mixture of delimited and positional records, providing a detailed XML representation of the flat-file FIN structures.</span></span>  

 <span data-ttu-id="d62e7-107">SWIFT 的大部分客戶會使用相對較小的子集的 SWIFT FIN 訊息。</span><span class="sxs-lookup"><span data-stu-id="d62e7-107">Most SWIFT customers use a relatively small subset of the SWIFT FIN messages.</span></span> <span data-ttu-id="d62e7-108">若要實作對於這些客戶的方案，您可以建立 BizTalk 結構描述專案 (如所示[模組 2： 加入新的結構描述專案](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)A4SWIFT 教學課程的)。</span><span class="sxs-lookup"><span data-stu-id="d62e7-108">To implement a solution for these customers, you can create a BizTalk schema project (as demonstrated in [Module 2: Adding a New Schemas Project](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md) of the A4SWIFT tutorial).</span></span> <span data-ttu-id="d62e7-109">新增相關的訊息結構描述 (MT*xxx*.xsd) 從\\\ Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category x\MT xyy 目錄，其中 x 是 FIN 訊息類型的第一個數字，而 xyy 是訊息的三位數的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d62e7-109">Add the relevant message schemas (MT*xxx*.xsd) from \\\ Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category x\MT xyy directory, where x is the first digit of the FIN message type and xyy is the three-digit message type for the message.</span></span>  

 <span data-ttu-id="d62e7-110">您可以將數個結構描述加入相同的專案。</span><span class="sxs-lookup"><span data-stu-id="d62e7-110">You can add several schemas to the same project.</span></span> <span data-ttu-id="d62e7-111">若要維護管理能力，您不應該新增 20 個以上的訊息結構描述，每個專案。</span><span class="sxs-lookup"><span data-stu-id="d62e7-111">To maintain manageability, you should not add more than 20 message schemas per project.</span></span> <span data-ttu-id="d62e7-112">您也需要將基底和通用的結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="d62e7-112">You also need to add the base and common schemas to the project.</span></span> <span data-ttu-id="d62e7-113">如果您已部署之基底和通用結構描述，您要建立其組件的參考，而不是將其部署。</span><span class="sxs-lookup"><span data-stu-id="d62e7-113">If you have already deployed the base and common schemas, you need to make a reference to their assembly, rather than deploy them.</span></span> <span data-ttu-id="d62e7-114">本章節描述這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="d62e7-114">This section describes these schemas.</span></span> <span data-ttu-id="d62e7-115">訊息結構描述已準備好使用，因為是傳送至 SWIFT 的網路訊息和接收自 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="d62e7-115">The message schemas are ready to use as is for both messages sent to the SWIFT network and messages received from SWIFT.</span></span>  

 <span data-ttu-id="d62e7-116">您可以檢查在 Microsoft 中的每個 SWIFT 結構描述的內容[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]使用結構描述編輯器。</span><span class="sxs-lookup"><span data-stu-id="d62e7-116">You can examine the contents of each SWIFT schema in Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] using the Schema Editor.</span></span> <span data-ttu-id="d62e7-117">所有訊息交換的結構描述有下列的一般結構：</span><span class="sxs-lookup"><span data-stu-id="d62e7-117">All of the message interchange schemas have the following common structure:</span></span>  

- <span data-ttu-id="d62e7-118">標頭</span><span class="sxs-lookup"><span data-stu-id="d62e7-118">Headers</span></span>  

- <span data-ttu-id="d62e7-119">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d62e7-119">Message text</span></span>  

- <span data-ttu-id="d62e7-120">結尾</span><span class="sxs-lookup"><span data-stu-id="d62e7-120">Trailers</span></span>  

  <span data-ttu-id="d62e7-121">本章節描述的標頭和結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="d62e7-121">This section describes the header and trailer schemas.</span></span> <span data-ttu-id="d62e7-122">訊息文字包含 FIN 訊息的承載，並包含的所有資料欄位包含寄件者、 接收者和訊息型別欄位除外。</span><span class="sxs-lookup"><span data-stu-id="d62e7-122">The message text comprises the payload of the FIN message, and contains all of the data fields except the fields containing the sender, receiver, and message type.</span></span> <span data-ttu-id="d62e7-123">這三個欄位都包含在標頭部分。</span><span class="sxs-lookup"><span data-stu-id="d62e7-123">These three fields are contained in the header portion.</span></span> <span data-ttu-id="d62e7-124">有些訊息也包含選擇性的使用者標頭，也會提供處理資訊。</span><span class="sxs-lookup"><span data-stu-id="d62e7-124">Some messages also contain an optional user header, which may also provide processing information.</span></span>  

  <span data-ttu-id="d62e7-125">每個 FIN 訊息內容是由一系列已定義的序列中的欄位所組成。</span><span class="sxs-lookup"><span data-stu-id="d62e7-125">Each FIN message payload consists of a series of fields in a defined sequence.</span></span> <span data-ttu-id="d62e7-126">這些欄位會符合下列規則：</span><span class="sxs-lookup"><span data-stu-id="d62e7-126">These fields conform to the following rules:</span></span>  

- <span data-ttu-id="d62e7-127">欄位可能是必要或選擇性序列內。</span><span class="sxs-lookup"><span data-stu-id="d62e7-127">The fields may be required or optional within the sequence.</span></span>  

- <span data-ttu-id="d62e7-128">序列可能包含子序列，並在順序中可能重複的子序列。</span><span class="sxs-lookup"><span data-stu-id="d62e7-128">A sequence may contain sub-sequences, and a sub-sequence may repeat within a sequence.</span></span>  

- <span data-ttu-id="d62e7-129">您可以使用數種訊息類型中的欄位。</span><span class="sxs-lookup"><span data-stu-id="d62e7-129">You can use a field in several message types.</span></span>  

- <span data-ttu-id="d62e7-130">在欄位中可能有項目或子欄位。</span><span class="sxs-lookup"><span data-stu-id="d62e7-130">Within a field, there may be elements or subfields.</span></span> <span data-ttu-id="d62e7-131">項目或子欄位可能是通用於數個欄位。</span><span class="sxs-lookup"><span data-stu-id="d62e7-131">An element or subfield may be common to several fields.</span></span>  

- <span data-ttu-id="d62e7-132">群組節點代表每個重複的序列。</span><span class="sxs-lookup"><span data-stu-id="d62e7-132">A group node represents each repeating sequence.</span></span>  

- <span data-ttu-id="d62e7-133">每個欄位可能本身有多個 nodal 層次，每個描述為一筆記錄。</span><span class="sxs-lookup"><span data-stu-id="d62e7-133">Each field may itself have multiple nodal levels, each described as a record.</span></span>  

- <span data-ttu-id="d62e7-134">結構描述項目代表只有最低層級子欄位。</span><span class="sxs-lookup"><span data-stu-id="d62e7-134">Schema elements represent only the lowest level subfields.</span></span>  

- <span data-ttu-id="d62e7-135">一般和基底結構描述定義一般記錄和項目。</span><span class="sxs-lookup"><span data-stu-id="d62e7-135">The common and base schemas define common records and elements.</span></span>  

- <span data-ttu-id="d62e7-136">結構描述代表某些欄位，以數種格式 （例如合作對象的欄位）。</span><span class="sxs-lookup"><span data-stu-id="d62e7-136">Schemas represent some fields in several formats (such as party fields).</span></span> <span data-ttu-id="d62e7-137">結構描述會定義這類欄位，為選項欄位。</span><span class="sxs-lookup"><span data-stu-id="d62e7-137">Schemas define such fields as choice fields.</span></span>  

- <span data-ttu-id="d62e7-138">某些欄位具有有限的一組值。</span><span class="sxs-lookup"><span data-stu-id="d62e7-138">Some fields have limited sets of values.</span></span> <span data-ttu-id="d62e7-139">大部分的情況下，結構描述會列出這些值。</span><span class="sxs-lookup"><span data-stu-id="d62e7-139">For the most part, the schema lists these values.</span></span> <span data-ttu-id="d62e7-140">結構描述定義也包含字元集驗證。</span><span class="sxs-lookup"><span data-stu-id="d62e7-140">Schema definitions also include character set validation.</span></span>  

  <span data-ttu-id="d62e7-141">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="d62e7-141">This section contains:</span></span>  

- [<span data-ttu-id="d62e7-142">基底和通用結構描述</span><span class="sxs-lookup"><span data-stu-id="d62e7-142">Base and Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  

- [<span data-ttu-id="d62e7-143">SWIFT 標頭和結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="d62e7-143">SWIFT Header and Trailer Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  

- [<span data-ttu-id="d62e7-144">SWIFT 結構描述命名慣例</span><span class="sxs-lookup"><span data-stu-id="d62e7-144">SWIFT Schema Naming Conventions</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)
