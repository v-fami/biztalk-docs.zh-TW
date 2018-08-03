---
title: 如何擱置協調流程執行個體或連接埠 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, suspending
- instances, suspending
- suspending
- HAT, suspending orchestrations
- HAT, suspending pipelines
- suspending, ports
- suspending, orchestrations
- orchestrations, suspending
- HAT, suspending ports
- suspending, instances
- ports, suspending
ms.assetid: cacc7e58-7d3e-4d6b-adb0-618fdc4f0d89
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10f6923df37b5cce3a500ed6e02014f09d1c2c0f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994927"
---
# <a name="how-to-suspend-orchestration-instances-or-ports"></a><span data-ttu-id="b0bcf-102">如何擱置協調流程執行個體或連接埠</span><span class="sxs-lookup"><span data-stu-id="b0bcf-102">How to Suspend Orchestration Instances or Ports</span></span>
<span data-ttu-id="b0bcf-103">您可以從 BizTalk Server 管理主控台的查詢結果清單中擱置協調流程執行個體或連接埠。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-103">You can suspend orchestration instances or ports from a query results list in the BizTalk Server Administration Console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b0bcf-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="b0bcf-104">Prerequisites</span></span>  
 <span data-ttu-id="b0bcf-105">您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-105">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-suspend-orchestration-instances-or-ports"></a><span data-ttu-id="b0bcf-106">擱置協調流程執行個體或連接埠</span><span class="sxs-lookup"><span data-stu-id="b0bcf-106">To suspend orchestration instances or ports</span></span>  
  
1. <span data-ttu-id="b0bcf-107">按一下 **開始**，按一下**程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-107">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="b0bcf-108">在主控台樹狀目錄中，依序展開**BizTalk Server 管理**，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-108">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3. <span data-ttu-id="b0bcf-109">在 詳細資料 窗格中，按一下**新的查詢** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-109">In the details pane, click the **New Query** tab.</span></span>  
  
4. <span data-ttu-id="b0bcf-110">在 **查詢運算式**群組中**值**欄中，選取**執行的服務執行個體**從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-110">In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.</span></span>  
  
5. <span data-ttu-id="b0bcf-111">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="b0bcf-111">Do one of the following:</span></span>  
  
   - <span data-ttu-id="b0bcf-112">若要暫停的單一執行個體，**欄位名**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **服務名稱</em>* 篩選器，然後在\*\*值*\* 欄中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-112">To suspend a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select the \**Service Name</em>* filter and then in the **Value** column, specify the service name.</span></span>  
  
   - <span data-ttu-id="b0bcf-113">若要暫停其大量執行個體，**欄位名稱**星號旁邊的空白下拉式清單方塊中的資料行 (**\\**<em>)，選取 **群組結果依據</em>* ，然後在\*\*值*\* 欄中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-113">To suspend instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\\**<em>), select \**Group Results By</em>* and then in the **Value** column, specify the service name.</span></span>  
  
6. <span data-ttu-id="b0bcf-114">按一下 **執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-114">Click **Run Query**.</span></span>  
  
7. <span data-ttu-id="b0bcf-115">在查詢結果清單中，以滑鼠右鍵按一下您想要暫停，然後按一下 作用中的協調流程或連接埠**暫止的執行個體**或是**擱置執行個體**。</span><span class="sxs-lookup"><span data-stu-id="b0bcf-115">In the query results list, right-click the active orchestration or port you want to suspend, and then click **Suspend Instance** or **Suspend Instances**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0bcf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0bcf-116">See Also</span></span>  
 [<span data-ttu-id="b0bcf-117">調查協調流程、連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="b0bcf-117">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)