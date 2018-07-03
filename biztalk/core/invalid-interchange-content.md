---
title: 無效的交換內容 |Microsoft Docs
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
ms.openlocfilehash: cc94b838a76b85c248322538328806520ad06723
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007617"
---
# <a name="invalid-interchange-content"></a><span data-ttu-id="b40ec-102">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="b40ec-102">Invalid Interchange Content</span></span>
## <a name="details"></a><span data-ttu-id="b40ec-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b40ec-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="b40ec-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b40ec-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="b40ec-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="b40ec-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="b40ec-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b40ec-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="b40ec-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="b40ec-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="b40ec-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="b40ec-108"> EDI</span></span> |
|    <span data-ttu-id="b40ec-109">元件</span><span class="sxs-lookup"><span data-stu-id="b40ec-109">Component</span></span>    |                                       <span data-ttu-id="b40ec-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="b40ec-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="b40ec-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b40ec-111">Symbolic Name</span></span>  |                       <span data-ttu-id="b40ec-112">X12Ta1InvalidInterchangeContentDescription</span><span class="sxs-lookup"><span data-stu-id="b40ec-112">X12Ta1InvalidInterchangeContentDescription</span></span>                       |
|  <span data-ttu-id="b40ec-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b40ec-113">Message Text</span></span>   |                              <span data-ttu-id="b40ec-114">無效的交換內容</span><span class="sxs-lookup"><span data-stu-id="b40ec-114">Invalid Interchange Content</span></span>                               |
  
## <a name="explanation"></a><span data-ttu-id="b40ec-115">說明</span><span class="sxs-lookup"><span data-stu-id="b40ec-115">Explanation</span></span>  
 <span data-ttu-id="b40ec-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換，或傳送管線無法處理外寄交換，因為交換中的資料未通過執行訊息驗證BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="b40ec-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange or the send pipeline could not process the outgoing interchange because the data in the interchange did not pass message validation performed by BizTalk Server.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b40ec-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b40ec-117">User Action</span></span>  
 <span data-ttu-id="b40ec-118">若要解決這個錯誤，交換的哪個部分，找出失敗的驗證，以及何種驗證失敗。</span><span class="sxs-lookup"><span data-stu-id="b40ec-118">To resolve this error, identify which part of the interchange failed validation, and which validation it failed.</span></span> <span data-ttu-id="b40ec-119">解決的問題，導致驗證失敗，並就會重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="b40ec-119">Resolve the issue that caused validation to fail, and then have the interchange resent.</span></span>