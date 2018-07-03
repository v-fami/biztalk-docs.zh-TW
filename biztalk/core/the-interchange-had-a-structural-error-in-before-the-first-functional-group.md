---
title: 交換發生結構錯誤的第一個功能群組之前 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 12202148-0a32-464e-8dbd-d01b9ba530eb
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04150fc8db853719517c26e7ae91a904e7096fb5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996655"
---
# <a name="the-interchange-had-a-structural-error-in-before-the-first-functional-group"></a><span data-ttu-id="f28c5-102">交換發生結構錯誤的第一個功能群組之前</span><span class="sxs-lookup"><span data-stu-id="f28c5-102">The interchange had a structural error in-before the first functional group</span></span>
## <a name="details"></a><span data-ttu-id="f28c5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f28c5-103">Details</span></span>  
  
|                 |                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="f28c5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f28c5-104">Product Name</span></span>   |                        [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                        |
| <span data-ttu-id="f28c5-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="f28c5-105">Product Version</span></span> |                                    [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                    |
|    <span data-ttu-id="f28c5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f28c5-106">Event ID</span></span>     |                                                                -                                                                 |
|  <span data-ttu-id="f28c5-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="f28c5-107">Event Source</span></span>   |                      [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f28c5-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="f28c5-108"> EDI</span></span>                      |
|    <span data-ttu-id="f28c5-109">元件</span><span class="sxs-lookup"><span data-stu-id="f28c5-109">Component</span></span>    |                                                            <span data-ttu-id="f28c5-110">將 EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="f28c5-110">EDI Engine</span></span>                                                            |
|  <span data-ttu-id="f28c5-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f28c5-111">Symbolic Name</span></span>  |                                           <span data-ttu-id="f28c5-112">X12InterchangeStructuralErrorBefore1stGroup</span><span class="sxs-lookup"><span data-stu-id="f28c5-112">X12InterchangeStructuralErrorBefore1stGroup</span></span>                                            |
|  <span data-ttu-id="f28c5-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f28c5-113">Message Text</span></span>   | <span data-ttu-id="f28c5-114">交換識別碼 '{0}'，寄件者識別碼為'{1}'，接收者識別碼 '{2}' 中/前第一次的功能群組發生結構錯誤</span><span class="sxs-lookup"><span data-stu-id="f28c5-114">The interchange with id '{0}', with sender id '{1}', receiver id '{2}' had structural error in/before the first functional group</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="f28c5-115">說明</span><span class="sxs-lookup"><span data-stu-id="f28c5-115">Explanation</span></span>  
 <span data-ttu-id="f28c5-116">這個錯誤/警告/資訊事件表示接收管線無法處理內送交換中，其中一個原因如下：</span><span class="sxs-lookup"><span data-stu-id="f28c5-116">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming interchange, for one of the following reasons:</span></span>  
  
-   <span data-ttu-id="f28c5-117">結構的錯誤發生的 ISA 和 IEA 區段或第一個功能群組的交換，因此適用的結構描述不符合交換。</span><span class="sxs-lookup"><span data-stu-id="f28c5-117">A structural error occurred in either the ISA and IEA segments or the first functional group of the interchange, so the interchange did not conform to the applicable schema.</span></span>  
  
-   <span data-ttu-id="f28c5-118">未部署的 X12ServiceSchema （在 BaseArtifacts.dll)。</span><span class="sxs-lookup"><span data-stu-id="f28c5-118">The X12ServiceSchema (in BaseArtifacts.dll) was not deployed.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f28c5-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f28c5-119">User Action</span></span>  
 <span data-ttu-id="f28c5-120">若要解決這個錯誤，請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="f28c5-120">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="f28c5-121">已交換變更 ISA 的寄件者和/或 IEA 區段或第一個功能群組，使其符合適用的結構描述，並再重新傳送交換。</span><span class="sxs-lookup"><span data-stu-id="f28c5-121">Have the sender of the interchange change the ISA and/or IEA segments or the first functional group so that it conforms to the applicable schema, and then resend the interchange.</span></span>  
  
-   <span data-ttu-id="f28c5-122">請確定 BaseArtifacts.dll 包含 X12ServiceSchema 和部署。</span><span class="sxs-lookup"><span data-stu-id="f28c5-122">Ensure that BaseArtifacts.dll includes the X12ServiceSchema and is deployed.</span></span> <span data-ttu-id="f28c5-123">您可以藉由開啟 BizTalk Server 管理主控台，開啟 BizTalk EDI 應用程式 節點和 結構描述 節點中，確認已列出 X12ServiceSchema 來這麼做。</span><span class="sxs-lookup"><span data-stu-id="f28c5-123">You can do so by opening the BizTalk Server Administration Console, opening the BizTalk EDI Application node and the Schemas node, and verifying that X12ServiceSchema is listed.</span></span>