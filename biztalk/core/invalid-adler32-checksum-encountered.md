---
title: "無效 Adler32 總和檢查碼遇到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa47a208-0f33-496e-8dbe-b50be9979bf2
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c069e6435c3840e9a535d492943dfc3956a513f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-adler32-checksum-encountered"></a><span data-ttu-id="f0b38-102">無效 Adler32 總和檢查碼遇到</span><span class="sxs-lookup"><span data-stu-id="f0b38-102">Invalid Adler32 checksum encountered</span></span>
## <a name="details"></a><span data-ttu-id="f0b38-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f0b38-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f0b38-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f0b38-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="f0b38-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f0b38-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="f0b38-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f0b38-106">Event ID</span></span>|-|  
|<span data-ttu-id="f0b38-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f0b38-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f0b38-108">EDI</span><span class="sxs-lookup"><span data-stu-id="f0b38-108"> EDI</span></span>|  
|<span data-ttu-id="f0b38-109">元件</span><span class="sxs-lookup"><span data-stu-id="f0b38-109">Component</span></span>|<span data-ttu-id="f0b38-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="f0b38-110">AS2 Engine</span></span>|  
|<span data-ttu-id="f0b38-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f0b38-111">Symbolic Name</span></span>|<span data-ttu-id="f0b38-112">InvalidAdler32ChecksumInCompressedMessageError</span><span class="sxs-lookup"><span data-stu-id="f0b38-112">InvalidAdler32ChecksumInCompressedMessageError</span></span>|  
|<span data-ttu-id="f0b38-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f0b38-113">Message Text</span></span>|<span data-ttu-id="f0b38-114">無效 Adler32 總和檢查碼遇到</span><span class="sxs-lookup"><span data-stu-id="f0b38-114">Invalid Adler32 checksum encountered</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f0b38-115">說明</span><span class="sxs-lookup"><span data-stu-id="f0b38-115">Explanation</span></span>  
 <span data-ttu-id="f0b38-116">這個錯誤是指 ASN.1 壓縮資料結構。</span><span class="sxs-lookup"><span data-stu-id="f0b38-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="f0b38-117">此錯誤表示壓縮資料寄件者可以是結構壓縮的資料不正確或沒有遭到竄改訊息 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="f0b38-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f0b38-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f0b38-118">User Action</span></span>  
 <span data-ttu-id="f0b38-119">使用**遇到無效的 Adler32 總和檢查碼**表示機率很高的資料遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="f0b38-119">The use of **Invalid Adler32 checksum encountered** indicates a high probability of tampering.</span></span> <span data-ttu-id="f0b38-120">檢查是否有遭到竄改，如果您看到**遇到無效的 Adler32 總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="f0b38-120">Check for tampering if you see **Invalid Adler32 checksum encountered**.</span></span>