---
title: 解壓縮處理過程中發現無效的 ASN.1 壓縮結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e5ebbd6-249a-4746-8ee6-cfb1f52ecc94
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07d1e44e38665a6a643131545afb660945a9f07e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969071"
---
# <a name="invalid-asn1-compressed-structure-encountered-during-decompression-processing"></a><span data-ttu-id="4f43d-102">解壓縮處理過程中發現無效的 ASN.1 壓縮結構</span><span class="sxs-lookup"><span data-stu-id="4f43d-102">Invalid ASN.1 compressed structure encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="4f43d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="4f43d-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="4f43d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="4f43d-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="4f43d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="4f43d-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="4f43d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4f43d-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="4f43d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="4f43d-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4f43d-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4f43d-108"> EDI</span></span> |
|    <span data-ttu-id="4f43d-109">元件</span><span class="sxs-lookup"><span data-stu-id="4f43d-109">Component</span></span>    |                                       <span data-ttu-id="4f43d-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="4f43d-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="4f43d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="4f43d-111">Symbolic Name</span></span>  |                       <span data-ttu-id="4f43d-112">InvalidASN1CompressedStructureEncountered</span><span class="sxs-lookup"><span data-stu-id="4f43d-112">InvalidASN1CompressedStructureEncountered</span></span>                        |
|  <span data-ttu-id="4f43d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="4f43d-113">Message Text</span></span>   | <span data-ttu-id="4f43d-114">解壓縮處理過程中發現無效或遺失的 ASN.1 壓縮標頭</span><span class="sxs-lookup"><span data-stu-id="4f43d-114">Invalid or missing ASN.1 compressed header encountered during decompression processing</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="4f43d-115">說明</span><span class="sxs-lookup"><span data-stu-id="4f43d-115">Explanation</span></span>  
 <span data-ttu-id="4f43d-116">此錯誤是指的 ASN.1 壓縮的資料結構。</span><span class="sxs-lookup"><span data-stu-id="4f43d-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="4f43d-117">此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="4f43d-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4f43d-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="4f43d-118">User Action</span></span>  
 <span data-ttu-id="4f43d-119">檢閱 壓縮的資料和檢查竄改訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="4f43d-119">Review the structure of the compressed data and check for tampering with the message.</span></span>