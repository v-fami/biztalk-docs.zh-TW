---
title: SWIFT 結尾 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SWIFT Trailer schema
- schemas, SWIFT
- trailers [SWIFT]
- SWIFT, trailers
ms.assetid: b6d64584-0514-4c87-98c0-33755efc4695
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc3155ac21f55e7c61483b9287429f9b722f6a84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214494"
---
# <a name="swift-trailers"></a><span data-ttu-id="4f0c6-102">SWIFT 結尾</span><span class="sxs-lookup"><span data-stu-id="4f0c6-102">SWIFT Trailers</span></span>
<span data-ttu-id="4f0c6-103">每個 SWIFT 的訊息都有一或多個結尾所需的訊息交換和安全性需求。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-103">Each SWIFT message has one or more trailers as required by the message exchange and security requirements.</span></span> <span data-ttu-id="4f0c6-104">系統結尾，如果適用的話，請遵循使用者結尾。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-104">System trailers, if applicable, follow user trailers.</span></span> <span data-ttu-id="4f0c6-105">結尾區塊內的每一個結尾會顯示進一步的成對的大括號以分隔的子區塊內。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-105">Each trailer within the Trailer Block appears within a subblock delimited by further pairs of curly brackets.</span></span> <span data-ttu-id="4f0c6-106">每一個子區塊的結尾類型，後面接著冒號的三個字母開頭。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-106">Each subblock begins with three letters denoting the trailer type, followed by a colon.</span></span>  
  
 <span data-ttu-id="4f0c6-107">SWIFT 結尾結構描述 (SWIFT Trailer.xsd) 包含下列格式：</span><span class="sxs-lookup"><span data-stu-id="4f0c6-107">The SWIFT Trailer schema (SWIFT Trailer.xsd) contains the format for the following:</span></span>  
  
-   <span data-ttu-id="4f0c6-108">文字區塊結束分隔符號</span><span class="sxs-lookup"><span data-stu-id="4f0c6-108">The ending delimiter of the text block</span></span>  
  
-   <span data-ttu-id="4f0c6-109">使用者結尾 （使用者和系統資訊）</span><span class="sxs-lookup"><span data-stu-id="4f0c6-109">User trailers (user and system information)</span></span>  
  
-   <span data-ttu-id="4f0c6-110">系統結尾</span><span class="sxs-lookup"><span data-stu-id="4f0c6-110">System trailers</span></span>  
  
 <span data-ttu-id="4f0c6-111">文字區塊的結束分隔符號是"-"}。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-111">The ending delimiter of the Text Block is "-}".</span></span> <span data-ttu-id="4f0c6-112">結尾區塊的開頭"{5:"。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-112">The trailer block begins with "{5:".</span></span> <span data-ttu-id="4f0c6-113">結尾區塊的內容會包含使用者資訊 （總和檢查碼、 訊息驗證，專屬的驗證，等等） 和系統資訊 （延遲的訊息，訊息參考，可能重複的訊息，以及等等）。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-113">The contents of the trailer block include both user information (checksum, message authentication, proprietary authentication, and so on), and system information (delayed message, message reference, possible duplicate message, and so on).</span></span> <span data-ttu-id="4f0c6-114">SWIFT 所加入的結尾也提供第三個區塊，以分隔"{S"。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-114">Trailers added by SWIFT also provide a third block, delimited by "{S:".</span></span> <span data-ttu-id="4f0c6-115">*SWIFT 使用者手冊*，「 尋找服務描述 」 主題，詳細說明區塊 5 的內容。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-115">The *SWIFT User Handbook*, "FIN Service Description" topic, describes in detail the contents of block 5.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="4f0c6-116">不會驗證 s 區塊的內容</span><span class="sxs-lookup"><span data-stu-id="4f0c6-116"> does not validate the contents of block S.</span></span>  
  
 <span data-ttu-id="4f0c6-117">實際的 FIN 介面或 SWIFT 網路將附加至結尾。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-117">The actual FIN interface or the SWIFT network appends the trailers.</span></span> <span data-ttu-id="4f0c6-118">如果訊息包含結尾時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收訊息，[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]帶有訊息結尾。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-118">If a message contains a trailer when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives the message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] carries the trailer with the message.</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="4f0c6-119">不會引發錯誤，如果訊息不包含結尾時[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]接收訊息。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-119"> does not raise an error if a message does not contain a trailer when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] receives the message.</span></span> <span data-ttu-id="4f0c6-120">做為具標頭，所有的結尾項目，包括區塊本身，都是選擇性中[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4f0c6-120">As with headers, all of the trailer entries, including the blocks themselves, are optional in [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)].</span></span>  
  
 <span data-ttu-id="4f0c6-121">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="4f0c6-121">This section contains:</span></span>  
  
-   [<span data-ttu-id="4f0c6-122">使用者結尾</span><span class="sxs-lookup"><span data-stu-id="4f0c6-122">User Trailers</span></span>](../../adapters-and-accelerators/accelerator-swift/user-trailers.md)  
  
-   [<span data-ttu-id="4f0c6-123">系統結尾</span><span class="sxs-lookup"><span data-stu-id="4f0c6-123">System Trailers</span></span>](../../adapters-and-accelerators/accelerator-swift/system-trailers.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f0c6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f0c6-124">See Also</span></span>  
 [<span data-ttu-id="4f0c6-125">使用結構描述</span><span class="sxs-lookup"><span data-stu-id="4f0c6-125">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)