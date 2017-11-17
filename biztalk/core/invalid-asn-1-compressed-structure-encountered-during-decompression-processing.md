---
title: "解壓縮處理過程中發現無效的 ASN.1 壓縮結構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e5ebbd6-249a-4746-8ee6-cfb1f52ecc94
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 825889d3379a4cbc1dc61bc688eb5ffc28745a5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-asn1-compressed-structure-encountered-during-decompression-processing"></a><span data-ttu-id="5fe86-102">解壓縮處理過程中發現無效的 ASN.1 壓縮結構</span><span class="sxs-lookup"><span data-stu-id="5fe86-102">Invalid ASN.1 compressed structure encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="5fe86-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5fe86-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fe86-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5fe86-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5fe86-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5fe86-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5fe86-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5fe86-106">Event ID</span></span>|-|  
|<span data-ttu-id="5fe86-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5fe86-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5fe86-108">EDI</span><span class="sxs-lookup"><span data-stu-id="5fe86-108"> EDI</span></span>|  
|<span data-ttu-id="5fe86-109">元件</span><span class="sxs-lookup"><span data-stu-id="5fe86-109">Component</span></span>|<span data-ttu-id="5fe86-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="5fe86-110">AS2 Engine</span></span>|  
|<span data-ttu-id="5fe86-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5fe86-111">Symbolic Name</span></span>|<span data-ttu-id="5fe86-112">InvalidASN1CompressedStructureEncountered</span><span class="sxs-lookup"><span data-stu-id="5fe86-112">InvalidASN1CompressedStructureEncountered</span></span>|  
|<span data-ttu-id="5fe86-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5fe86-113">Message Text</span></span>|<span data-ttu-id="5fe86-114">解壓縮處理過程中發現無效或遺失的 ASN.1 壓縮標頭</span><span class="sxs-lookup"><span data-stu-id="5fe86-114">Invalid or missing ASN.1 compressed header encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5fe86-115">說明</span><span class="sxs-lookup"><span data-stu-id="5fe86-115">Explanation</span></span>  
 <span data-ttu-id="5fe86-116">這個錯誤是指 ASN.1 壓縮資料結構。</span><span class="sxs-lookup"><span data-stu-id="5fe86-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="5fe86-117">此錯誤表示壓縮資料寄件者可以是結構壓縮的資料不正確或沒有遭到竄改訊息 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="5fe86-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5fe86-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5fe86-118">User Action</span></span>  
 <span data-ttu-id="5fe86-119">檢閱 壓縮的資料和檢查竄改訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="5fe86-119">Review the structure of the compressed data and check for tampering with the message.</span></span>