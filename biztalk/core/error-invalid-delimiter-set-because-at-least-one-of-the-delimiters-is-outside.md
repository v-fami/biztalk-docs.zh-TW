---
title: 無效的分隔符號集，因為至少其中一個分隔符號是允許的範圍之外 |Microsoft Docs
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
ms.openlocfilehash: ebda7e3ebfe2adc0084b672a2f66ed1ad639c943
ms.sourcegitcommit: c3070a7a3f332857357f056dc632829b43869c17
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2018
ms.locfileid: "51630363"
---
# <a name="invalid-delimiter-set-because-at-least-one-of-the-delimiters-is-outside-the-allowed-range"></a><span data-ttu-id="42983-102">無效的分隔符號集，因為至少其中一個分隔符號是在允許的範圍之外</span><span class="sxs-lookup"><span data-stu-id="42983-102">Invalid delimiter set because at least one of the delimiters is outside the allowed range</span></span>
## <a name="details"></a><span data-ttu-id="42983-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="42983-103">Details</span></span>  
  
|                 |                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="42983-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="42983-104">Product Name</span></span>   |           [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]           |
| <span data-ttu-id="42983-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="42983-105">Product Version</span></span> |                       [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                       |
|    <span data-ttu-id="42983-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="42983-106">Event ID</span></span>     |                                                   -                                                    |
|  <span data-ttu-id="42983-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="42983-107">Event Source</span></span>   |         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] <span data-ttu-id="42983-108">EDI</span><span class="sxs-lookup"><span data-stu-id="42983-108">EDI</span></span>         |
|    <span data-ttu-id="42983-109">元件</span><span class="sxs-lookup"><span data-stu-id="42983-109">Component</span></span>    |                                               <span data-ttu-id="42983-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="42983-110">EDI Engine</span></span>                                               |
|  <span data-ttu-id="42983-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="42983-111">Symbolic Name</span></span>  |                                          <span data-ttu-id="42983-112">DelimiterOutOfRange</span><span class="sxs-lookup"><span data-stu-id="42983-112">DelimiterOutOfRange</span></span>                                           |
|  <span data-ttu-id="42983-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="42983-113">Message Text</span></span>   | <span data-ttu-id="42983-114">無效的分隔符號集{0}，其中至少一個分隔符號是允許的 0 到 127 的範圍之外</span><span class="sxs-lookup"><span data-stu-id="42983-114">Invalid delimiter set {0}, at least one of the delimiters is outside the allowed range of 0 through 127</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="42983-115">說明</span><span class="sxs-lookup"><span data-stu-id="42983-115">Explanation</span></span>  
 <span data-ttu-id="42983-116">這個錯誤/警告/資訊事件表示，接收管線無法處理內送交換因為交換中的一或多個分隔符號中的 ASCII 字元的值範圍以外設定。</span><span class="sxs-lookup"><span data-stu-id="42983-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange because one or more separators in the interchange was outside the range of values in the ASCII character set.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="42983-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="42983-117">User Action</span></span>  
 <span data-ttu-id="42983-118">若要解決這個錯誤，請確定交換中的每個分隔符號為 ASCII 字元集，，，然後重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="42983-118">To resolve this error, make sure that each separator in the interchange is in the ASCII character set, and then have the interchange resent.</span></span>
