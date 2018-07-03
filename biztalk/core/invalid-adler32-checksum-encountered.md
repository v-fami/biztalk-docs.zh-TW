---
title: 遇到無效的 Adler32 checksum |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa47a208-0f33-496e-8dbe-b50be9979bf2
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acaa60e9d6f1bda4161832cb5ddb34c4e2e9ae93
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987263"
---
# <a name="invalid-adler32-checksum-encountered"></a><span data-ttu-id="e5f05-102">無效 Adler32 總和檢查碼時發生</span><span class="sxs-lookup"><span data-stu-id="e5f05-102">Invalid Adler32 checksum encountered</span></span>
## <a name="details"></a><span data-ttu-id="e5f05-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e5f05-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e5f05-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e5f05-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e5f05-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e5f05-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e5f05-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e5f05-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e5f05-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e5f05-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e5f05-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e5f05-108"> EDI</span></span> |
|    <span data-ttu-id="e5f05-109">元件</span><span class="sxs-lookup"><span data-stu-id="e5f05-109">Component</span></span>    |                                       <span data-ttu-id="e5f05-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="e5f05-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="e5f05-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e5f05-111">Symbolic Name</span></span>  |                     <span data-ttu-id="e5f05-112">InvalidAdler32ChecksumInCompressedMessageError</span><span class="sxs-lookup"><span data-stu-id="e5f05-112">InvalidAdler32ChecksumInCompressedMessageError</span></span>                     |
|  <span data-ttu-id="e5f05-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e5f05-113">Message Text</span></span>   |                          <span data-ttu-id="e5f05-114">無效 Adler32 總和檢查碼時發生</span><span class="sxs-lookup"><span data-stu-id="e5f05-114">Invalid Adler32 checksum encountered</span></span>                          |
  
## <a name="explanation"></a><span data-ttu-id="e5f05-115">說明</span><span class="sxs-lookup"><span data-stu-id="e5f05-115">Explanation</span></span>  
 <span data-ttu-id="e5f05-116">此錯誤是指的 ASN.1 壓縮的資料結構。</span><span class="sxs-lookup"><span data-stu-id="e5f05-116">This error refers to the ASN.1 structure of the compressed data.</span></span> <span data-ttu-id="e5f05-117">此錯誤表示寄件者的壓縮資料可以結構壓縮的資料不正確或沒有訊息遭到竄改 （未經授權的變更）。</span><span class="sxs-lookup"><span data-stu-id="e5f05-117">The error indicates the sender of the compressed data either structured the compressed data incorrectly or there was tampering (unauthorized change) of the message.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e5f05-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e5f05-118">User Action</span></span>  
 <span data-ttu-id="e5f05-119">善用**發現無效的 Adler32 總和檢查碼**表示較高的機率的竄改。</span><span class="sxs-lookup"><span data-stu-id="e5f05-119">The use of **Invalid Adler32 checksum encountered** indicates a high probability of tampering.</span></span> <span data-ttu-id="e5f05-120">檢查是否有遭到竄改，如果您看到**發現無效的 Adler32 總和檢查碼**。</span><span class="sxs-lookup"><span data-stu-id="e5f05-120">Check for tampering if you see **Invalid Adler32 checksum encountered**.</span></span>