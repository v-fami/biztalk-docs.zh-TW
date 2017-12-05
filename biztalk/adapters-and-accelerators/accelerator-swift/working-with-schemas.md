---
title: "使用結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, schemas
- schemas, developing
ms.assetid: 123c4b43-34e4-41c7-980d-5d518b1479c1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 404beaeb617f7a6c0c5e3fc4ddc40126e6b97990
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="working-with-schemas"></a><span data-ttu-id="974c1-102">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="974c1-102">Working with Schemas</span></span>
<span data-ttu-id="974c1-103">中提供的結構描述[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]協會全球 Interbank 財務 Telecommunication (SWIFT) FIN 訊息的 XSD 表示法。</span><span class="sxs-lookup"><span data-stu-id="974c1-103">The schemas provided in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] XSD representation of the Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages.</span></span> <span data-ttu-id="974c1-104">每個訊息類型都有自己的結構描述，包括 SWIFT 標頭和 SWIFT trailer （交換格式）。</span><span class="sxs-lookup"><span data-stu-id="974c1-104">Each message type has its own schema, including the SWIFT header and SWIFT trailer (interchange format).</span></span> <span data-ttu-id="974c1-105">此結構描述便可傳送或接收 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="974c1-105">This schema is sufficient to send or receive a SWIFT message.</span></span> <span data-ttu-id="974c1-106">這些結構描述是唯一的分隔和位置記錄，以提供詳細的 XML 表示法，一般檔案 FIN 結構的混合。</span><span class="sxs-lookup"><span data-stu-id="974c1-106">These schemas are a unique mixture of delimited and positional records, providing a detailed XML representation of the flat-file FIN structures.</span></span>  
  
 <span data-ttu-id="974c1-107">大部分的 SWIFT 客戶使用 SWIFT FIN 訊息相對較小的子集。</span><span class="sxs-lookup"><span data-stu-id="974c1-107">Most SWIFT customers use a relatively small subset of the SWIFT FIN messages.</span></span> <span data-ttu-id="974c1-108">若要實作解決方案，這些客戶，您可以建立 BizTalk 結構描述專案 (如所示[單元 2： 加入新的結構描述專案](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md)A4SWIFT 教學課程的)。</span><span class="sxs-lookup"><span data-stu-id="974c1-108">To implement a solution for these customers, you can create a BizTalk schema project (as demonstrated in [Module 2: Adding a New Schemas Project](../../adapters-and-accelerators/accelerator-swift/module-2-adding-a-new-schemas-project.md) of the A4SWIFT tutorial).</span></span> <span data-ttu-id="974c1-109">新增相關的訊息結構描述 (MT*xxx*.xsd) 從\\\ Program Files\Microsoft BizTalk Accelerator for SWIFT\<版本\>MessagePack\SWIFT Messages\A4SWIFT SRG\<版本\>\Category x\MT xyy 目錄，其中 x 是 FIN 訊息類型的第一個數字，而 xyy 是訊息的三位數的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="974c1-109">Add the relevant message schemas (MT*xxx*.xsd) from \\\ Program Files\Microsoft BizTalk Accelerator for SWIFT \<version\> MessagePack\SWIFT Messages\A4SWIFT-SRG\<version\>\Category x\MT xyy directory, where x is the first digit of the FIN message type and xyy is the three-digit message type for the message.</span></span>  
  
 <span data-ttu-id="974c1-110">您可以將數個結構描述加入至相同的專案。</span><span class="sxs-lookup"><span data-stu-id="974c1-110">You can add several schemas to the same project.</span></span> <span data-ttu-id="974c1-111">若要維護可管理性，您不應該新增 20 個以上的訊息結構描述，每個專案。</span><span class="sxs-lookup"><span data-stu-id="974c1-111">To maintain manageability, you should not add more than 20 message schemas per project.</span></span> <span data-ttu-id="974c1-112">您也需要將基底且常見的結構描述加入至專案。</span><span class="sxs-lookup"><span data-stu-id="974c1-112">You also need to add the base and common schemas to the project.</span></span> <span data-ttu-id="974c1-113">如果您已部署的基底且常見的結構描述，您需要在它們的組件參考，而不是將其部署。</span><span class="sxs-lookup"><span data-stu-id="974c1-113">If you have already deployed the base and common schemas, you need to make a reference to their assembly, rather than deploy them.</span></span> <span data-ttu-id="974c1-114">本章節描述這些結構描述。</span><span class="sxs-lookup"><span data-stu-id="974c1-114">This section describes these schemas.</span></span> <span data-ttu-id="974c1-115">訊息結構描述就可以開始使用，因為是 SWIFT 網路傳送的訊息和接收來自 SWIFT 的訊息。</span><span class="sxs-lookup"><span data-stu-id="974c1-115">The message schemas are ready to use as is for both messages sent to the SWIFT network and messages received from SWIFT.</span></span>  
  
 <span data-ttu-id="974c1-116">您可以檢查每個 SWIFT 的結構描述中的內容[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] [!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)]使用結構描述編輯器。</span><span class="sxs-lookup"><span data-stu-id="974c1-116">You can examine the contents of each SWIFT schema in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)][!INCLUDE[btsDotNet](../../includes/btsdotnet-md.md)] using the Schema Editor.</span></span> <span data-ttu-id="974c1-117">所有訊息交換的結構描述有下列的一般結構：</span><span class="sxs-lookup"><span data-stu-id="974c1-117">All of the message interchange schemas have the following common structure:</span></span>  
  
-   <span data-ttu-id="974c1-118">標頭</span><span class="sxs-lookup"><span data-stu-id="974c1-118">Headers</span></span>  
  
-   <span data-ttu-id="974c1-119">訊息文字</span><span class="sxs-lookup"><span data-stu-id="974c1-119">Message text</span></span>  
  
-   <span data-ttu-id="974c1-120">結尾</span><span class="sxs-lookup"><span data-stu-id="974c1-120">Trailers</span></span>  
  
 <span data-ttu-id="974c1-121">本章節描述的標頭和結尾結構描述。</span><span class="sxs-lookup"><span data-stu-id="974c1-121">This section describes the header and trailer schemas.</span></span> <span data-ttu-id="974c1-122">訊息文字包含 FIN 訊息的裝載和包含的所有資料欄位包含寄件者、 接收者和訊息類型的欄位除外。</span><span class="sxs-lookup"><span data-stu-id="974c1-122">The message text comprises the payload of the FIN message, and contains all of the data fields except the fields containing the sender, receiver, and message type.</span></span> <span data-ttu-id="974c1-123">這三個欄位都包含在標頭部分。</span><span class="sxs-lookup"><span data-stu-id="974c1-123">These three fields are contained in the header portion.</span></span> <span data-ttu-id="974c1-124">有些訊息也包含選擇性的使用者標頭，也會提供處理資訊。</span><span class="sxs-lookup"><span data-stu-id="974c1-124">Some messages also contain an optional user header, which may also provide processing information.</span></span>  
  
 <span data-ttu-id="974c1-125">每個 FIN 訊息內容是由一系列的定義順序中的欄位所組成。</span><span class="sxs-lookup"><span data-stu-id="974c1-125">Each FIN message payload consists of a series of fields in a defined sequence.</span></span> <span data-ttu-id="974c1-126">這些欄位符合下列規則：</span><span class="sxs-lookup"><span data-stu-id="974c1-126">These fields conform to the following rules:</span></span>  
  
-   <span data-ttu-id="974c1-127">欄位是必要或選擇性在序列。</span><span class="sxs-lookup"><span data-stu-id="974c1-127">The fields may be required or optional within the sequence.</span></span>  
  
-   <span data-ttu-id="974c1-128">序列可能包含子序列，與子序列可能會重複序列中。</span><span class="sxs-lookup"><span data-stu-id="974c1-128">A sequence may contain sub-sequences, and a sub-sequence may repeat within a sequence.</span></span>  
  
-   <span data-ttu-id="974c1-129">您可以使用數種訊息類型中的欄位。</span><span class="sxs-lookup"><span data-stu-id="974c1-129">You can use a field in several message types.</span></span>  
  
-   <span data-ttu-id="974c1-130">在欄位中，可能會有項目或子欄位。</span><span class="sxs-lookup"><span data-stu-id="974c1-130">Within a field, there may be elements or subfields.</span></span> <span data-ttu-id="974c1-131">項目或子欄位可能是通用於數個欄位。</span><span class="sxs-lookup"><span data-stu-id="974c1-131">An element or subfield may be common to several fields.</span></span>  
  
-   <span data-ttu-id="974c1-132">群組節點代表每個重複的序列。</span><span class="sxs-lookup"><span data-stu-id="974c1-132">A group node represents each repeating sequence.</span></span>  
  
-   <span data-ttu-id="974c1-133">每個欄位可能本身會有多個 nodal 等級，以記錄每個所述。</span><span class="sxs-lookup"><span data-stu-id="974c1-133">Each field may itself have multiple nodal levels, each described as a record.</span></span>  
  
-   <span data-ttu-id="974c1-134">結構描述項目代表只最低的層級子欄位。</span><span class="sxs-lookup"><span data-stu-id="974c1-134">Schema elements represent only the lowest level subfields.</span></span>  
  
-   <span data-ttu-id="974c1-135">在一般和基底結構描述會定義一般記錄和項目。</span><span class="sxs-lookup"><span data-stu-id="974c1-135">The common and base schemas define common records and elements.</span></span>  
  
-   <span data-ttu-id="974c1-136">結構描述代表許多格式 （例如合作對象的欄位） 中的某些欄位。</span><span class="sxs-lookup"><span data-stu-id="974c1-136">Schemas represent some fields in several formats (such as party fields).</span></span> <span data-ttu-id="974c1-137">結構描述會定義這類欄位做為選擇的欄位。</span><span class="sxs-lookup"><span data-stu-id="974c1-137">Schemas define such fields as choice fields.</span></span>  
  
-   <span data-ttu-id="974c1-138">某些欄位具有有限的一組值。</span><span class="sxs-lookup"><span data-stu-id="974c1-138">Some fields have limited sets of values.</span></span> <span data-ttu-id="974c1-139">大部分的情況下，結構描述會列出這些值。</span><span class="sxs-lookup"><span data-stu-id="974c1-139">For the most part, the schema lists these values.</span></span> <span data-ttu-id="974c1-140">結構描述定義也包含字元集驗證。</span><span class="sxs-lookup"><span data-stu-id="974c1-140">Schema definitions also include character set validation.</span></span>  
  
 <span data-ttu-id="974c1-141">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="974c1-141">This section contains:</span></span>  
  
-   [<span data-ttu-id="974c1-142">基底和通用結構描述</span><span class="sxs-lookup"><span data-stu-id="974c1-142">Base and Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/base-and-common-schemas.md)  
  
-   [<span data-ttu-id="974c1-143">SWIFT 標頭和結尾結構描述</span><span class="sxs-lookup"><span data-stu-id="974c1-143">SWIFT Header and Trailer Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-header-and-trailer-schemas.md)  
  
-   [<span data-ttu-id="974c1-144">SWIFT 結構描述命名慣例</span><span class="sxs-lookup"><span data-stu-id="974c1-144">SWIFT Schema Naming Conventions</span></span>](../../adapters-and-accelerators/accelerator-swift/swift-schema-naming-conventions.md)