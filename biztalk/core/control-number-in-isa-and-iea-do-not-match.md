---
title: ISA 和 IEA 中的控制編號不相符 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f9091ea-460b-464b-acd5-8dc0488b61e5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd2f86d767b6065a6aeaa02f887dc8b6bd056fbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237902"
---
# <a name="control-number-in-isa-and-iea-do-not-match"></a><span data-ttu-id="c60af-102">ISA 和 IEA 中的控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="c60af-102">Control Number in ISA and IEA do not match</span></span>
## <a name="details"></a><span data-ttu-id="c60af-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c60af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c60af-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c60af-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c60af-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c60af-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c60af-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c60af-106">Event ID</span></span>|-|  
|<span data-ttu-id="c60af-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c60af-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c60af-108">EDI</span><span class="sxs-lookup"><span data-stu-id="c60af-108"> EDI</span></span>|  
|<span data-ttu-id="c60af-109">元件</span><span class="sxs-lookup"><span data-stu-id="c60af-109">Component</span></span>|<span data-ttu-id="c60af-110">AS2 引擎</span><span class="sxs-lookup"><span data-stu-id="c60af-110">AS2 Engine</span></span>|  
|<span data-ttu-id="c60af-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c60af-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="c60af-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c60af-112">Message Text</span></span>|<span data-ttu-id="c60af-113">ISA 和 IEA 中的控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="c60af-113">Control Number in ISA and IEA do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c60af-114">說明</span><span class="sxs-lookup"><span data-stu-id="c60af-114">Explanation</span></span>  
 <span data-ttu-id="c60af-115">這個錯誤/警告/資訊事件表示，由於包含在內送交換之 [ISA13] 和 [IEA02] 欄位中的交換控制編號值不同，因此 AS2 接收管線無法處理該交換。</span><span class="sxs-lookup"><span data-stu-id="c60af-115">This Error/Warning/Information event indicates that the AS2 receive pipeline could not process the incoming interchange because the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange do not have the same value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c60af-116">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c60af-116">User Action</span></span>  
 <span data-ttu-id="c60af-117">若要解決這個錯誤，請確定 ISA13] 和 [IEA02 交換的欄位中包含的交換控制編號具有相同的值，並接著必須重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c60af-117">To resolve this error, make sure that the interchange control numbers contained in the ISA13 and IEA02 fields of the interchange have the same value, and then have the interchange resent.</span></span>