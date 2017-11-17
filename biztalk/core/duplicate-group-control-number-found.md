---
title: "重複的群組控制編號找到 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1badc033-42fd-4992-ad36-b53047ba7817
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9165414d1a9a743c77c28b087730745d3dcc4c0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="duplicate-group-control-number-found"></a><span data-ttu-id="a0601-102">找到重複的群組控制編號</span><span class="sxs-lookup"><span data-stu-id="a0601-102">Duplicate group control number found</span></span>
## <a name="details"></a><span data-ttu-id="a0601-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a0601-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a0601-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a0601-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="a0601-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="a0601-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="a0601-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a0601-106">Event ID</span></span>|-|  
|<span data-ttu-id="a0601-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="a0601-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a0601-108">EDI</span><span class="sxs-lookup"><span data-stu-id="a0601-108"> EDI</span></span>|  
|<span data-ttu-id="a0601-109">元件</span><span class="sxs-lookup"><span data-stu-id="a0601-109">Component</span></span>|<span data-ttu-id="a0601-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="a0601-110">EDI Engine</span></span>|  
|<span data-ttu-id="a0601-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a0601-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="a0601-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a0601-112">Message Text</span></span>|<span data-ttu-id="a0601-113">找到重複的群組控制編號</span><span class="sxs-lookup"><span data-stu-id="a0601-113">Duplicate group control number found</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a0601-114">說明</span><span class="sxs-lookup"><span data-stu-id="a0601-114">Explanation</span></span>  
 <span data-ttu-id="a0601-115">這個錯誤/警告/資訊事件表示 EDI 接收管線無法不處理內送交換因為它的相同交換、 群組或交易集控制編號和先前已接收交換。</span><span class="sxs-lookup"><span data-stu-id="a0601-115">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming interchange because it had the same interchange, group, or transaction set control number as a previously received interchange.</span></span> <span data-ttu-id="a0601-116">只要適當的重複控制編號檢查已啟用，這會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="a0601-116">This will result in a failure as long as the appropriate duplicate control number checks are enabled.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a0601-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a0601-117">User Action</span></span>  
 <span data-ttu-id="a0601-118">若要解決這個錯誤，執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="a0601-118">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="a0601-119">請確定傳送至 BizTalk Server 的交換，並沒有相同的群組控制編號和之前的交換，如果對應的重複控制編號檢查已啟用。</span><span class="sxs-lookup"><span data-stu-id="a0601-119">Ensure that the interchange sent to BizTalk Server does not have the same group control number as a previous interchange, if the corresponding duplicate control number check is enabled.</span></span>  
  
-   <span data-ttu-id="a0601-120">停用重複群組控制編號檢查。</span><span class="sxs-lookup"><span data-stu-id="a0601-120">Disable the duplicate group control number check.</span></span> <span data-ttu-id="a0601-121">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下適當的合作對象，然後開啟 [EDIFACT 交換處理屬性] 或 [X12 交換處理屬性] 對話方塊的合作對象做為交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="a0601-121">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the appropriate party, and open either the EDIFACT Interchange Processing Properties or the X12 Interchange Processing Properties dialog box for the party as an interchange sender.</span></span> <span data-ttu-id="a0601-122">若要停用檢查 EDIFACT 交換，清除 檢查重複項目 UNG5 （群組控制編號） 交換屬性中。</span><span class="sxs-lookup"><span data-stu-id="a0601-122">To disable a check for an EDIFACT interchange, clear the Check for duplicate UNG5 (Group control number) in interchange property.</span></span> <span data-ttu-id="a0601-123">若要停用檢查的 X12 交換，請清除核取的重複 GS6 （群組控制編號） 交換屬性中。</span><span class="sxs-lookup"><span data-stu-id="a0601-123">To disable a check for an X12 interchange, clear the Check for duplicate GS6 (Group control number) in interchange property.</span></span>