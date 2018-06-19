---
title: 無效或遺失的 ASN.1 壓縮資料 OID 解壓縮處理過程中發現 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0171daa8-289a-43f1-8cbf-d779ef9dc2ea
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05af1fc0c9f6516f180cf629cd0a21d838f0b4f0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241750"
---
# <a name="invalid-or-missing-asn1-compressed-data-oid-encountered-during-decompression-processing"></a><span data-ttu-id="6541b-102">無效或遺失的 ASN.1 壓縮資料 OID 解壓縮處理過程中發現</span><span class="sxs-lookup"><span data-stu-id="6541b-102">Invalid or missing ASN.1 Compressed Data OID encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="6541b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="6541b-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6541b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="6541b-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6541b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="6541b-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6541b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="6541b-106">Event ID</span></span>|-|  
|<span data-ttu-id="6541b-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="6541b-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6541b-108">EDI</span><span class="sxs-lookup"><span data-stu-id="6541b-108"> EDI</span></span>|  
|<span data-ttu-id="6541b-109">元件</span><span class="sxs-lookup"><span data-stu-id="6541b-109">Component</span></span>|<span data-ttu-id="6541b-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="6541b-110">AS2 Engine</span></span>|  
|<span data-ttu-id="6541b-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="6541b-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="6541b-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="6541b-112">Message Text</span></span>|<span data-ttu-id="6541b-113">無效或遺失的 ASN.1 壓縮資料 OID 解壓縮處理過程中發現</span><span class="sxs-lookup"><span data-stu-id="6541b-113">Invalid or missing ASN.1 Compressed Data OID encountered during decompression processing</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6541b-114">說明</span><span class="sxs-lookup"><span data-stu-id="6541b-114">Explanation</span></span>  
 <span data-ttu-id="6541b-115">這個錯誤是指 ASN.1 壓縮資料結構。</span><span class="sxs-lookup"><span data-stu-id="6541b-115">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="6541b-116">此錯誤表示壓縮資料寄件者可以是結構壓縮的資料不正確或沒有遭到竄改訊息 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="6541b-116">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6541b-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="6541b-117">User Action</span></span>  
 <span data-ttu-id="6541b-118">檢閱 壓縮的資料和檢查竄改訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="6541b-118">Review the structure of the compressed data and check for tampering with the message.</span></span>