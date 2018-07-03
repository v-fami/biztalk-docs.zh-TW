---
title: 解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7caf047-badd-49e8-b955-554e5ec7511f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d1ee1388304eb9923dcd2c6fef1468794f7c622a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012847"
---
# <a name="invalid-asn1-zlib-compression-field-encountered-during-decompression-processing"></a><span data-ttu-id="2576c-102">解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位</span><span class="sxs-lookup"><span data-stu-id="2576c-102">Invalid ASN.1 ZLib compression field encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="2576c-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2576c-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="2576c-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2576c-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="2576c-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2576c-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="2576c-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2576c-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="2576c-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="2576c-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2576c-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="2576c-108"> EDI</span></span> |
|    <span data-ttu-id="2576c-109">元件</span><span class="sxs-lookup"><span data-stu-id="2576c-109">Component</span></span>    |                                       <span data-ttu-id="2576c-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="2576c-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="2576c-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2576c-111">Symbolic Name</span></span>  |                          <span data-ttu-id="2576c-112">InvalidOptionalZLibFieldEncountered</span><span class="sxs-lookup"><span data-stu-id="2576c-112">InvalidOptionalZLibFieldEncountered</span></span>                           |
|  <span data-ttu-id="2576c-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2576c-113">Message Text</span></span>   |    <span data-ttu-id="2576c-114">解壓縮處理過程中發現無效的 ASN.1 ZLib 壓縮欄位</span><span class="sxs-lookup"><span data-stu-id="2576c-114">Invalid ASN.1 ZLib compression field encountered during decompression processing</span></span>    |
  
## <a name="explanation"></a><span data-ttu-id="2576c-115">說明</span><span class="sxs-lookup"><span data-stu-id="2576c-115">Explanation</span></span>  
 <span data-ttu-id="2576c-116">此錯誤是指的 ASN.1 壓縮的資料結構。</span><span class="sxs-lookup"><span data-stu-id="2576c-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="2576c-117">此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="2576c-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2576c-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2576c-118">User Action</span></span>  
 <span data-ttu-id="2576c-119">檢閱 壓縮的資料，並檢查被竄改的辨識項的結構。</span><span class="sxs-lookup"><span data-stu-id="2576c-119">Review the structure of the compressed data and check for evidence of tampering.</span></span>