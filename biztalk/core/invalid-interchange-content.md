---
title: 無效的交換內容 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b2352c3-d233-4d79-be31-b32dde29c8ee
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d03dc518406083cda1b070a3358cc4d8967f5f07
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257022"
---
# <a name="invalid-interchange-content"></a><span data-ttu-id="013c4-102">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="013c4-102">Invalid Interchange Content</span></span>
## <a name="details"></a><span data-ttu-id="013c4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="013c4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="013c4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="013c4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="013c4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="013c4-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="013c4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="013c4-106">Event ID</span></span>|-|  
|<span data-ttu-id="013c4-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="013c4-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="013c4-108">EDI</span><span class="sxs-lookup"><span data-stu-id="013c4-108"> EDI</span></span>|  
|<span data-ttu-id="013c4-109">元件</span><span class="sxs-lookup"><span data-stu-id="013c4-109">Component</span></span>|<span data-ttu-id="013c4-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="013c4-110">EDI Engine</span></span>|  
|<span data-ttu-id="013c4-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="013c4-111">Symbolic Name</span></span>|<span data-ttu-id="013c4-112">X12Ta1InvalidInterchangeContentDescription</span><span class="sxs-lookup"><span data-stu-id="013c4-112">X12Ta1InvalidInterchangeContentDescription</span></span>|  
|<span data-ttu-id="013c4-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="013c4-113">Message Text</span></span>|<span data-ttu-id="013c4-114">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="013c4-114">Invalid Interchange Content</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="013c4-115">說明</span><span class="sxs-lookup"><span data-stu-id="013c4-115">Explanation</span></span>  
 <span data-ttu-id="013c4-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為交換中的資料未通過執行訊息驗證BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="013c4-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the data in the interchange did not pass message validation performed by BizTalk Server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="013c4-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="013c4-117">User Action</span></span>  
 <span data-ttu-id="013c4-118">解決這個錯誤，交換的哪個部分，找出失敗的驗證，並讓驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="013c4-118">To resolve this error, identify which part of the interchange failed validation, and which validation it failed.</span></span> <span data-ttu-id="013c4-119">解決的問題，導致驗證失敗，並接著必須重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="013c4-119">Resolve the issue that caused validation to fail, and then have the interchange resent.</span></span>