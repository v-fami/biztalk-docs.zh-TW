---
title: 區段具有尾端分隔符號，在元件或子元件層級 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 517f1cfc-66c1-47e6-be94-2c76c1f89230
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3eede2923da1ed206a897b879b7b6be589800e4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269662"
---
# <a name="segment-has-trailing-delimiters-at-component-or-sub-component-level"></a><span data-ttu-id="d5850-102">區段具有尾端分隔符號，在元件或子元件層級</span><span class="sxs-lookup"><span data-stu-id="d5850-102">Segment has trailing delimiter(s) at component or sub-component level</span></span>
## <a name="details"></a><span data-ttu-id="d5850-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d5850-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d5850-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d5850-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d5850-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d5850-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d5850-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d5850-106">Event ID</span></span>|-|  
|<span data-ttu-id="d5850-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d5850-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d5850-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d5850-108"> EDI</span></span>|  
|<span data-ttu-id="d5850-109">元件</span><span class="sxs-lookup"><span data-stu-id="d5850-109">Component</span></span>|<span data-ttu-id="d5850-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d5850-110">EDI Engine</span></span>|  
|<span data-ttu-id="d5850-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d5850-111">Symbolic Name</span></span>|<span data-ttu-id="d5850-112">X12SeSegmentHasTrailingDelimiterDescription</span><span class="sxs-lookup"><span data-stu-id="d5850-112">X12SeSegmentHasTrailingDelimiterDescription</span></span>|  
|<span data-ttu-id="d5850-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d5850-113">Message Text</span></span>|<span data-ttu-id="d5850-114">區段具有尾端分隔符號，在元件或子元件層級</span><span class="sxs-lookup"><span data-stu-id="d5850-114">Segment has trailing delimiter(s) at component or sub-component level</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d5850-115">說明</span><span class="sxs-lookup"><span data-stu-id="d5850-115">Explanation</span></span>  
 <span data-ttu-id="d5850-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換，因為交換包含尾端分隔符號，但未啟用做為交換傳送者合作對象的尾端分隔符號。</span><span class="sxs-lookup"><span data-stu-id="d5850-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contained trailing delimiters, but trailing delimiters were not enabled for the party as interchange sender.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d5850-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d5850-117">User Action</span></span>  
 <span data-ttu-id="d5850-118">若要解決這個錯誤，啟用 尾端分隔符號，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d5850-118">To resolve this error, enable trailing separators as follows:</span></span>  
  
1.  <span data-ttu-id="d5850-119">開啟 BizTalk Server 管理主控台，移至 合作對象 資料夾中，並開啟 EDI 屬性的合作對象。</span><span class="sxs-lookup"><span data-stu-id="d5850-119">Open the BizTalk Server Administration Console, move to the Parties folder, and open the EDI Properties for the party.</span></span>  
  
2.  <span data-ttu-id="d5850-120">移至 驗證和通知產生頁面的 X12 或 EDIFACT，視需要。</span><span class="sxs-lookup"><span data-stu-id="d5850-120">Move to the Validation and ACK Generation page for X12 or EDIFACT, as appropriate.</span></span>  
  
3.  <span data-ttu-id="d5850-121">按一下 [允許尾端分隔符號]。</span><span class="sxs-lookup"><span data-stu-id="d5850-121">Click "Allow trailing separators".</span></span>