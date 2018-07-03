---
title: 解壓縮處理過程中發現的無效或遺失的 ASN.1 資料長度欄位 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cd08648d-77b9-42a3-a50e-fd87eb36758a
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aaab2fa12fc9d175c237224128055081d596962
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994471"
---
# <a name="invalid-or-missing-asn1-data-length-field-encountered-during-decompression-processing"></a><span data-ttu-id="e39c4-102">解壓縮處理過程中發現的無效或遺失的 ASN.1 資料長度欄位</span><span class="sxs-lookup"><span data-stu-id="e39c4-102">Invalid or missing ASN.1 Data Length field encountered during decompression processing</span></span>
## <a name="details"></a><span data-ttu-id="e39c4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e39c4-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e39c4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e39c4-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e39c4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e39c4-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e39c4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e39c4-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e39c4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e39c4-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e39c4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e39c4-108"> EDI</span></span> |
|    <span data-ttu-id="e39c4-109">元件</span><span class="sxs-lookup"><span data-stu-id="e39c4-109">Component</span></span>    |                                       <span data-ttu-id="e39c4-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="e39c4-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="e39c4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e39c4-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="e39c4-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e39c4-112">Message Text</span></span>   | <span data-ttu-id="e39c4-113">解壓縮處理過程中發現的無效或遺失的 ASN.1 資料長度欄位</span><span class="sxs-lookup"><span data-stu-id="e39c4-113">Invalid or missing ASN.1 Data Length field encountered during decompression processing</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="e39c4-114">說明</span><span class="sxs-lookup"><span data-stu-id="e39c4-114">Explanation</span></span>  
 <span data-ttu-id="e39c4-115">此錯誤是指的 ASN.1 壓縮的資料結構。</span><span class="sxs-lookup"><span data-stu-id="e39c4-115">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="e39c4-116">此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="e39c4-116">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e39c4-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e39c4-117">User Action</span></span>  
 <span data-ttu-id="e39c4-118">檢閱 壓縮的資料和檢查竄改訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="e39c4-118">Review the structure of the compressed data and check for tampering with the message.</span></span>