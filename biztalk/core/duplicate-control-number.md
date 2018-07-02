---
title: 重複的控制編號 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 331ad173-29b3-427c-8104-60d80c580a5a
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcfd1a10b836ec593b6aa94a87d8145d6e2ebaaf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967887"
---
# <a name="duplicate-control-number"></a><span data-ttu-id="de4af-102">重複的控制編號</span><span class="sxs-lookup"><span data-stu-id="de4af-102">Duplicate Control Number</span></span>
## <a name="details"></a><span data-ttu-id="de4af-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="de4af-103">Details</span></span>  

|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  <span data-ttu-id="de4af-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="de4af-104">Product Name</span></span>   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| <span data-ttu-id="de4af-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="de4af-105">Product Version</span></span> |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    <span data-ttu-id="de4af-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="de4af-106">Event ID</span></span>     |                                           -                                            |
|  <span data-ttu-id="de4af-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="de4af-107">Event Source</span></span>   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="de4af-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="de4af-108"> EDI</span></span> |
|    <span data-ttu-id="de4af-109">元件</span><span class="sxs-lookup"><span data-stu-id="de4af-109">Component</span></span>    |                                       <span data-ttu-id="de4af-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="de4af-110">EDI Engine</span></span>                                       |
|  <span data-ttu-id="de4af-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="de4af-111">Symbolic Name</span></span>  |                                           -                                            |
|  <span data-ttu-id="de4af-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="de4af-112">Message Text</span></span>   |                                <span data-ttu-id="de4af-113">重複的控制編號</span><span class="sxs-lookup"><span data-stu-id="de4af-113">Duplicate Control Number</span></span>                                |

## <a name="explanation"></a><span data-ttu-id="de4af-114">說明</span><span class="sxs-lookup"><span data-stu-id="de4af-114">Explanation</span></span>  
 <span data-ttu-id="de4af-115">這個錯誤/警告/資訊事件表示 EDI 接收管線無法不處理內送交換因為它有相同的交換、 群組或交易集控制編號和先前已接收的交換。</span><span class="sxs-lookup"><span data-stu-id="de4af-115">This Error/Warning/Information event indicates that the EDI receive pipeline could not process an incoming interchange because it had the same interchange, group, or transaction set control number as a previously received interchange.</span></span> <span data-ttu-id="de4af-116">只要啟用適當的重複控制編號檢查，這會導致失敗。</span><span class="sxs-lookup"><span data-stu-id="de4af-116">This will result in a failure as long as the appropriate duplicate control number checks are enabled.</span></span>  

## <a name="user-action"></a><span data-ttu-id="de4af-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="de4af-117">User Action</span></span>  
 <span data-ttu-id="de4af-118">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="de4af-118">To resolve this error, do one of the following:</span></span>  

- <span data-ttu-id="de4af-119">如果對應的重複控制編號檢查已啟用，請確認傳送至 BizTalk Server 之交換的交換、群組或交易集控制編號和之前的交換不同。</span><span class="sxs-lookup"><span data-stu-id="de4af-119">Ensure that the interchange sent to BizTalk Server does not have the same interchange, group, or transaction set control number as a previous interchange, if the corresponding duplicate control number check is enabled.</span></span>  

- <span data-ttu-id="de4af-120">停用重複控制編號檢查。</span><span class="sxs-lookup"><span data-stu-id="de4af-120">Disable the duplicate control number check.</span></span> <span data-ttu-id="de4af-121">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下適當的合作對象，然後開啟 [EDIFACT 交換處理屬性] 或 [X12 交換處理屬性] 對話方塊中，做為交換傳送者合作對象。</span><span class="sxs-lookup"><span data-stu-id="de4af-121">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the appropriate party, and open either the EDIFACT Interchange Processing Properties or the X12 Interchange Processing Properties dialog box for the party as an interchange sender.</span></span> <span data-ttu-id="de4af-122">若要停用 EDIFACT 交換的檢查，請清除 [檢查重複項目 UNB5 (交換控制編號)]、[檢查交換中的重複項目 UNG5 (群組控制編號)] 或 [檢查群組中的重複項目 UNH1 (交易集參考編號)] 屬性。</span><span class="sxs-lookup"><span data-stu-id="de4af-122">To disable a check for an EDIFACT interchange, clear the Check for duplicate UNB5 (Interchange control number), Check for duplicate UNG5 (Group control number) in interchange, or Check for duplicate UNH1 (Transaction set reference number) in group property.</span></span> <span data-ttu-id="de4af-123">若要停用 X12 交換的檢查，請清除 [檢查重複項目 ISA13 (交換控制編號)]、[檢查交換中的重複項目 GS6 (群組控制編號)] 或 [檢查群組中的重複項目 ST2 (交易集控制編號)] 屬性。</span><span class="sxs-lookup"><span data-stu-id="de4af-123">To disable a check for an X12 interchange, clear the Check for duplicate ISA13 (Interchange control number), Check for duplicate GS6 (Group control number) in interchange, or Check for duplicate ST2 (Transaction set control number) in group property.</span></span>
