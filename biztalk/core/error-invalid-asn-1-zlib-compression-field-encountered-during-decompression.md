---
title: "解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b7caf047-badd-49e8-b955-554e5ec7511f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a347f63325e1c93497d178ffcc486ff8bd1c4f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-asn1-zlib-compression-field-encountered-during-decompression-processing"></a><span data-ttu-id="f28ab-102">解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位</span><span class="sxs-lookup"><span data-stu-id="f28ab-102">Invalid ASN.1 ZLib compression field encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="f28ab-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f28ab-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f28ab-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f28ab-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f28ab-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f28ab-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f28ab-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f28ab-106">Event ID</span></span>|-|  
|<span data-ttu-id="f28ab-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f28ab-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f28ab-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f28ab-108"> EDI</span></span>|  
|<span data-ttu-id="f28ab-109">元件</span><span class="sxs-lookup"><span data-stu-id="f28ab-109">Component</span></span>|<span data-ttu-id="f28ab-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="f28ab-110">AS2 Engine</span></span>|  
|<span data-ttu-id="f28ab-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f28ab-111">Symbolic Name</span></span>|<span data-ttu-id="f28ab-112">InvalidOptionalZLibFieldEncountered</span><span class="sxs-lookup"><span data-stu-id="f28ab-112">InvalidOptionalZLibFieldEncountered</span></span>|  
|<span data-ttu-id="f28ab-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f28ab-113">Message Text</span></span>|<span data-ttu-id="f28ab-114">解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位</span><span class="sxs-lookup"><span data-stu-id="f28ab-114">Invalid ASN.1 ZLib compression field encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f28ab-115">說明</span><span class="sxs-lookup"><span data-stu-id="f28ab-115">Explanation</span></span>  
 <span data-ttu-id="f28ab-116">這個錯誤是指 ASN.1 壓縮資料結構。</span><span class="sxs-lookup"><span data-stu-id="f28ab-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="f28ab-117">此錯誤表示壓縮資料寄件者可以是結構壓縮的資料不正確或沒有遭到竄改訊息 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="f28ab-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f28ab-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f28ab-118">User Action</span></span>  
 <span data-ttu-id="f28ab-119">檢閱 壓縮的資料和檢查被竄改的辨識項的結構。</span><span class="sxs-lookup"><span data-stu-id="f28ab-119">Review the structure of the compressed data and check for evidence of tampering.</span></span>