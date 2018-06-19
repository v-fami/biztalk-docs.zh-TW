---
title: 未預期的區段 |Microsoft 文件
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
ms.openlocfilehash: 47ff173b88c51ecf28a4979cef3a0c61475c62c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286470"
---
# <a name="unexpected-segment"></a><span data-ttu-id="d586d-102">未預期的區段</span><span class="sxs-lookup"><span data-stu-id="d586d-102">Unexpected segment</span></span>
## <a name="details"></a><span data-ttu-id="d586d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d586d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d586d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d586d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="d586d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="d586d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="d586d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d586d-106">Event ID</span></span>|-|  
|<span data-ttu-id="d586d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="d586d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d586d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="d586d-108"> EDI</span></span>|  
|<span data-ttu-id="d586d-109">元件</span><span class="sxs-lookup"><span data-stu-id="d586d-109">Component</span></span>|<span data-ttu-id="d586d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="d586d-110">EDI Engine</span></span>|  
|<span data-ttu-id="d586d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d586d-111">Symbolic Name</span></span>|<span data-ttu-id="d586d-112">X12UnexpectedSegmentDescription</span><span class="sxs-lookup"><span data-stu-id="d586d-112">X12UnexpectedSegmentDescription</span></span>|  
|<span data-ttu-id="d586d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d586d-113">Message Text</span></span>|<span data-ttu-id="d586d-114">未預期的區段</span><span class="sxs-lookup"><span data-stu-id="d586d-114">Unexpected segment</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d586d-115">說明</span><span class="sxs-lookup"><span data-stu-id="d586d-115">Explanation</span></span>  
 <span data-ttu-id="d586d-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為此交換包含不由文件結構描述或服務結構描述定義的區段。</span><span class="sxs-lookup"><span data-stu-id="d586d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because the interchange contains a segment that is not defined by either the document schema or the service schema.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d586d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d586d-117">User Action</span></span>  
 <span data-ttu-id="d586d-118">若要解決這個錯誤，交換移除未預期的區段，交換的寄件者後再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="d586d-118">To resolve this error, have the sender of the interchange remove the unexpected segment from the interchange, and then resend the interchange.</span></span>