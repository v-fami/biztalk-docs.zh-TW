---
title: "回條傳遞選項值無效 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0eed306b-0912-4694-a55c-976128117c02
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f14541cd9c296e6a4527e7c2958123e072be8c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receipt-delivery-option-value-is-invalid"></a><span data-ttu-id="78578-102">回條傳遞選項值無效</span><span class="sxs-lookup"><span data-stu-id="78578-102">Receipt-Delivery-Option value is invalid</span></span>
## <a name="details"></a><span data-ttu-id="78578-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="78578-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78578-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="78578-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="78578-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="78578-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="78578-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="78578-106">Event ID</span></span>|-|  
|<span data-ttu-id="78578-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="78578-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="78578-108">EDI</span><span class="sxs-lookup"><span data-stu-id="78578-108"> EDI</span></span>|  
|<span data-ttu-id="78578-109">元件</span><span class="sxs-lookup"><span data-stu-id="78578-109">Component</span></span>|<span data-ttu-id="78578-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="78578-110">AS2 Engine</span></span>|  
|<span data-ttu-id="78578-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="78578-111">Symbolic Name</span></span>|<span data-ttu-id="78578-112">InvalidReceiptDeliveryOptionError</span><span class="sxs-lookup"><span data-stu-id="78578-112">InvalidReceiptDeliveryOptionError</span></span>|  
|<span data-ttu-id="78578-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="78578-113">Message Text</span></span>|<span data-ttu-id="78578-114">回條傳遞選項的值:"{0}"無效。</span><span class="sxs-lookup"><span data-stu-id="78578-114">Receipt-Delivery-Option value: "{0}" is invalid.</span></span>  <span data-ttu-id="78578-115">{1}</span><span class="sxs-lookup"><span data-stu-id="78578-115">{1}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="78578-116">說明</span><span class="sxs-lookup"><span data-stu-id="78578-116">Explanation</span></span>  
 <span data-ttu-id="78578-117">這個錯誤/警告/資訊事件表示接收傳遞選項中收到的 AS2 訊息不是有效的 URL，而且不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="78578-117">This Error/Warning/Information event indicates that the Receipt-Delivery-Option in the received AS2 message is not a valid URL and does not conform to the specifications in the AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="78578-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="78578-118">User Action</span></span>  
 <span data-ttu-id="78578-119">若要解決這個錯誤，請變更為包含有效的 URL 和符合 AS2 RFC 4130 7.3 節中的規格，然後重新傳送 AS2 訊息的 AS2 訊息中有回條傳遞選項。</span><span class="sxs-lookup"><span data-stu-id="78578-119">To resolve this error, have the Receipt-Delivery-Option in the AS2 message changed to include a valid URL and conform to the specifications in section 7.3 of the AS2 RFC 4130, and then resend the AS2 message.</span></span>