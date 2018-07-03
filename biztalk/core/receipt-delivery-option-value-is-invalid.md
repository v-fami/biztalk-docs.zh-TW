---
title: 回條傳遞選項的值無效 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0eed306b-0912-4694-a55c-976128117c02
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8966e3d95e89aff023300a9834ab1bca2915421f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994847"
---
# <a name="receipt-delivery-option-value-is-invalid"></a><span data-ttu-id="e765a-102">回條傳遞選項的值無效</span><span class="sxs-lookup"><span data-stu-id="e765a-102">Receipt-Delivery-Option value is invalid</span></span>
## <a name="details"></a><span data-ttu-id="e765a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e765a-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="e765a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e765a-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="e765a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e765a-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="e765a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e765a-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="e765a-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e765a-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e765a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="e765a-108"> EDI</span></span> |
|    <span data-ttu-id="e765a-109">元件</span><span class="sxs-lookup"><span data-stu-id="e765a-109">Component</span></span>    |                                       <span data-ttu-id="e765a-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="e765a-110">AS2 Engine</span></span>                                       |
|  <span data-ttu-id="e765a-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e765a-111">Symbolic Name</span></span>  |                           <span data-ttu-id="e765a-112">InvalidReceiptDeliveryOptionError</span><span class="sxs-lookup"><span data-stu-id="e765a-112">InvalidReceiptDeliveryOptionError</span></span>                            |
|  <span data-ttu-id="e765a-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e765a-113">Message Text</span></span>   |                 <span data-ttu-id="e765a-114">回條傳遞選項值:"{0}"無效。</span><span class="sxs-lookup"><span data-stu-id="e765a-114">Receipt-Delivery-Option value: "{0}" is invalid.</span></span>  <span data-ttu-id="e765a-115">{1}</span><span class="sxs-lookup"><span data-stu-id="e765a-115">{1}</span></span>                  |
  
## <a name="explanation"></a><span data-ttu-id="e765a-116">說明</span><span class="sxs-lookup"><span data-stu-id="e765a-116">Explanation</span></span>  
 <span data-ttu-id="e765a-117">這個錯誤/警告/資訊事件表示回條傳遞選項中收到的 AS2 訊息不是有效的 URL，且不符合 AS2 RFC 4130 中的規格。</span><span class="sxs-lookup"><span data-stu-id="e765a-117">This Error/Warning/Information event indicates that the Receipt-Delivery-Option in the received AS2 message is not a valid URL and does not conform to the specifications in the AS2 RFC 4130.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e765a-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e765a-118">User Action</span></span>  
 <span data-ttu-id="e765a-119">若要解決這個錯誤，請變更為包含有效的 URL 和符合 AS2 RFC 4130 7.3 節中的規格，然後重新傳送 AS2 訊息的 AS2 訊息中有回條傳遞選項。</span><span class="sxs-lookup"><span data-stu-id="e765a-119">To resolve this error, have the Receipt-Delivery-Option in the AS2 message changed to include a valid URL and conform to the specifications in section 7.3 of the AS2 RFC 4130, and then resend the AS2 message.</span></span>