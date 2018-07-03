---
title: 未預期的區段 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7169190c-8893-4076-8634-137fd43992f2
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d493647a184a250120ee25e614deb82c2f062d2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998839"
---
# <a name="unexpected-segment"></a><span data-ttu-id="3a75e-102">未預期的區段</span><span class="sxs-lookup"><span data-stu-id="3a75e-102">Unexpected segment</span></span>
## <a name="details"></a><span data-ttu-id="3a75e-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3a75e-103">Details</span></span>  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="3a75e-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3a75e-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="3a75e-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3a75e-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="3a75e-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3a75e-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="3a75e-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3a75e-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3a75e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="3a75e-108"> EDI</span></span> |
|    <span data-ttu-id="3a75e-109">元件</span><span class="sxs-lookup"><span data-stu-id="3a75e-109">Component</span></span>    |                                       <span data-ttu-id="3a75e-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3a75e-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="3a75e-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3a75e-111">Symbolic Name</span></span>  |                            <span data-ttu-id="3a75e-112">X12UnexpectedSegmentDescription</span><span class="sxs-lookup"><span data-stu-id="3a75e-112">X12UnexpectedSegmentDescription</span></span>                             |
|  <span data-ttu-id="3a75e-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3a75e-113">Message Text</span></span>   |                                   <span data-ttu-id="3a75e-114">未預期的區段</span><span class="sxs-lookup"><span data-stu-id="3a75e-114">Unexpected segment</span></span>                                   |
  
## <a name="explanation"></a><span data-ttu-id="3a75e-115">說明</span><span class="sxs-lookup"><span data-stu-id="3a75e-115">Explanation</span></span>  
 <span data-ttu-id="3a75e-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中包含的文件結構描述或服務結構描述未定義的區段。</span><span class="sxs-lookup"><span data-stu-id="3a75e-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contains a segment that is not defined by either the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3a75e-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3a75e-117">User Action</span></span>  
 <span data-ttu-id="3a75e-118">若要解決這個錯誤，將傳送者的交換移除從交換中，未預期的區段與然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="3a75e-118">To resolve this error, have the sender of the interchange remove the unexpected segment from the interchange, and then resend the interchange.</span></span>