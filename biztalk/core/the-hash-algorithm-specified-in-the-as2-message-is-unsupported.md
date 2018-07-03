---
title: 不支援 AS2 訊息中指定的雜湊演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b292238-f964-4275-bbfa-e21c9150abf7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c3c46f65fb71ef810fc4e657df01e0065757cae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008591"
---
# <a name="the-hash-algorithm-specified-in-the-as2-message-is-unsupported"></a><span data-ttu-id="85c30-102">不支援 AS2 訊息中指定的雜湊演算法</span><span class="sxs-lookup"><span data-stu-id="85c30-102">The hash algorithm specified in the AS2 message is unsupported</span></span>
## <a name="details"></a><span data-ttu-id="85c30-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="85c30-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="85c30-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="85c30-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="85c30-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="85c30-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="85c30-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="85c30-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="85c30-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="85c30-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="85c30-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="85c30-108"> EDI</span></span> |
|    <span data-ttu-id="85c30-109">元件</span><span class="sxs-lookup"><span data-stu-id="85c30-109">Component</span></span>    |                                       <span data-ttu-id="85c30-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="85c30-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="85c30-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="85c30-111">Symbolic Name</span></span>  |                            <span data-ttu-id="85c30-112">UnsupportedAS2HashAlgorithmError</span><span class="sxs-lookup"><span data-stu-id="85c30-112">UnsupportedAS2HashAlgorithmError</span></span>                            |
|  <span data-ttu-id="85c30-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="85c30-113">Message Text</span></span>   |            <span data-ttu-id="85c30-114">不支援 AS2 訊息中指定的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="85c30-114">The hash algorithm specified in the AS2 message is unsupported.</span></span>             |
  
## <a name="explanation"></a><span data-ttu-id="85c30-115">說明</span><span class="sxs-lookup"><span data-stu-id="85c30-115">Explanation</span></span>  
 <span data-ttu-id="85c30-116">這個錯誤/警告/資訊事件表示，接收管線無法產生 MDN 所指定因為收到的 AS2 訊息的簽署回條 micalg 標頭中指定的 MIC 雜湊演算法不是有效的值。</span><span class="sxs-lookup"><span data-stu-id="85c30-116">This Error/Warning/Information event indicates that the receive pipeline could not generate the MDN as specified because the MIC hash algorithm specified in the signed-receipt-micalg header of the received AS2 message is not a valid value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="85c30-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="85c30-117">User Action</span></span>  
 <span data-ttu-id="85c30-118">若要解決這個錯誤，將傳送者的訊息變更演算法 MD5 或 SHA1，與重新傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="85c30-118">To resolve this error, have the sender of the message change the algorithm to either MD5 or SHA1, and resend the message.</span></span>