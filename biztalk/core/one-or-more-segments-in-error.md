---
title: 一或多個區段發生錯誤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4ee86667-e72a-4f1b-8d5c-15ca710dbe5d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 340c722bc96ec8efdf2f48e6b40260aa5323e675
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263366"
---
# <a name="one-or-more-segments-in-error"></a><span data-ttu-id="3c266-102">一或多個區段發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3c266-102">One or more segments in error</span></span>
## <a name="details"></a><span data-ttu-id="3c266-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3c266-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c266-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3c266-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3c266-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="3c266-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="3c266-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3c266-106">Event ID</span></span>|-|  
|<span data-ttu-id="3c266-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="3c266-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="3c266-108">EDI</span><span class="sxs-lookup"><span data-stu-id="3c266-108"> EDI</span></span>|  
|<span data-ttu-id="3c266-109">元件</span><span class="sxs-lookup"><span data-stu-id="3c266-109">Component</span></span>|<span data-ttu-id="3c266-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="3c266-110">EDI Engine</span></span>|  
|<span data-ttu-id="3c266-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3c266-111">Symbolic Name</span></span>|<span data-ttu-id="3c266-112">X12TsOneOrMoreSegmentsInErrorDescription</span><span class="sxs-lookup"><span data-stu-id="3c266-112">X12TsOneOrMoreSegmentsInErrorDescription</span></span>|  
|<span data-ttu-id="3c266-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3c266-113">Message Text</span></span>|<span data-ttu-id="3c266-114">一或多個區段發生錯誤</span><span class="sxs-lookup"><span data-stu-id="3c266-114">One or more segments in error</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3c266-115">說明</span><span class="sxs-lookup"><span data-stu-id="3c266-115">Explanation</span></span>  
 <span data-ttu-id="3c266-116">這個錯誤/警告/資訊事件表示，來管理它們的結構描述不符合交換中的一個或多個區段。</span><span class="sxs-lookup"><span data-stu-id="3c266-116">This Error/Warning/Information event indicates that one or more segments in the interchange did not conform to the schema governing them.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3c266-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3c266-117">User Action</span></span>  
 <span data-ttu-id="3c266-118">若要解決這個錯誤，判斷哪一個區段中錯誤、 開啟結構描述控管該區段，並從該區段處於錯誤的結構描述判斷。</span><span class="sxs-lookup"><span data-stu-id="3c266-118">To resolve this error, determine which segment is in error, open the schema governing that segment, and determine from that schema why the segment is in error.</span></span>