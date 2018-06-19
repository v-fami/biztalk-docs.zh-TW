---
title: GS 和 GE 的群組控制編號不相符 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2419f61-2717-4347-a4be-54362330c7e3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05bb9e879e9a994215ba052fc3549d5bdb28e9fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246174"
---
# <a name="group-control-number-in-gs-and-ge-do-not-match"></a><span data-ttu-id="c458d-102">GS 和 GE 的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="c458d-102">Group control number in GS and GE do not match</span></span>
## <a name="details"></a><span data-ttu-id="c458d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c458d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c458d-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c458d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="c458d-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="c458d-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="c458d-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c458d-106">Event ID</span></span>|-|  
|<span data-ttu-id="c458d-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="c458d-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="c458d-108">EDI</span><span class="sxs-lookup"><span data-stu-id="c458d-108"> EDI</span></span>|  
|<span data-ttu-id="c458d-109">元件</span><span class="sxs-lookup"><span data-stu-id="c458d-109">Component</span></span>|<span data-ttu-id="c458d-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="c458d-110">EDI Engine</span></span>|  
|<span data-ttu-id="c458d-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c458d-111">Symbolic Name</span></span>|<span data-ttu-id="c458d-112">X12FaControlNumberMismatchDescription</span><span class="sxs-lookup"><span data-stu-id="c458d-112">X12FaControlNumberMismatchDescription</span></span>|  
|<span data-ttu-id="c458d-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c458d-113">Message Text</span></span>|<span data-ttu-id="c458d-114">GS 和 GE 的群組控制編號不相符</span><span class="sxs-lookup"><span data-stu-id="c458d-114">Group control number in GS and GE do not match</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c458d-115">說明</span><span class="sxs-lookup"><span data-stu-id="c458d-115">Explanation</span></span>  
 <span data-ttu-id="c458d-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送 X12 交換，因為 GS06 和 GE02 交換的欄位中包含的控制編號沒有相同的值。</span><span class="sxs-lookup"><span data-stu-id="c458d-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming X12 interchange because the control numbers contained in the GS06 and GE02 fields of the  interchange do not have the same value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c458d-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c458d-117">User Action</span></span>  
 <span data-ttu-id="c458d-118">若要解決這個錯誤，請確定 GS06 和 GE02 交換的欄位中包含的群組控制編號具有相同的值，並接著必須重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="c458d-118">To resolve this error, make sure that the group control numbers contained in the GS06 and GE02 fields of the interchange have the same value, and then have the interchange resent.</span></span>