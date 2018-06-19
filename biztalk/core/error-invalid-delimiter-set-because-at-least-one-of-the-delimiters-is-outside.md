---
title: 無效的分隔符號設定，因為至少其中一個分隔符號是允許的範圍以外 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1286559-765b-4728-945d-cf3386e1ba06
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c70722adc1a099d340b862d38574b44391954aa4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241454"
---
# <a name="invalid-delimiter-set-because-at-least-one-of-the-delimiters-is-outside-the-allowed-range"></a><span data-ttu-id="5a863-102">無效的分隔符號集，因為至少其中一個分隔符號是在允許的範圍之外</span><span class="sxs-lookup"><span data-stu-id="5a863-102">Invalid delimiter set because at least one of the delimiters is outside the allowed range</span></span>
## <a name="details"></a><span data-ttu-id="5a863-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="5a863-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5a863-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="5a863-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5a863-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="5a863-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5a863-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="5a863-106">Event ID</span></span>|-|  
|<span data-ttu-id="5a863-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="5a863-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5a863-108">EDI</span><span class="sxs-lookup"><span data-stu-id="5a863-108"> EDI</span></span>|  
|<span data-ttu-id="5a863-109">元件</span><span class="sxs-lookup"><span data-stu-id="5a863-109">Component</span></span>|<span data-ttu-id="5a863-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="5a863-110">EDI Engine</span></span>|  
|<span data-ttu-id="5a863-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="5a863-111">Symbolic Name</span></span>|<span data-ttu-id="5a863-112">DelimiterOutOfRange</span><span class="sxs-lookup"><span data-stu-id="5a863-112">DelimiterOutOfRange</span></span>|  
|<span data-ttu-id="5a863-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="5a863-113">Message Text</span></span>|<span data-ttu-id="5a863-114">無效的分隔符號設定 {0}，至少其中一個分隔符號是 0 到 127 的容許範圍外</span><span class="sxs-lookup"><span data-stu-id="5a863-114">Invalid delimiter set {0}, atleast one of the delimiters is outside the allowed range of 0 through 127</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5a863-115">說明</span><span class="sxs-lookup"><span data-stu-id="5a863-115">Explanation</span></span>  
 <span data-ttu-id="5a863-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的一個或多個分隔字元的 ASCII 字元集中的值範圍以外設定。</span><span class="sxs-lookup"><span data-stu-id="5a863-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because one or more separators in the interchange was outside the range of values in the ASCII character set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5a863-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="5a863-117">User Action</span></span>  
 <span data-ttu-id="5a863-118">若要解決這個錯誤，請確定到交換中的每個分隔字元是 ASCII 字元集，，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="5a863-118">To resolve this error, make sure that each separator in the interchange is in the ASCII character set, and then have the interchange resent.</span></span>