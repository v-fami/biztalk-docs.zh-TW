---
title: 如何擱置協調流程執行個體或連接埠 |Microsoft 文件
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
ms.openlocfilehash: 62d91c8d1e02b7283a430f7c82c572b6a989d108
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22256694"
---
# <a name="how-to-suspend-orchestration-instances-or-ports"></a><span data-ttu-id="a7dec-102">如何擱置協調流程執行個體或連接埠</span><span class="sxs-lookup"><span data-stu-id="a7dec-102">How to Suspend Orchestration Instances or Ports</span></span>
<span data-ttu-id="a7dec-103">您可以從 BizTalk Server 管理主控台的查詢結果清單中擱置協調流程執行個體或連接埠。</span><span class="sxs-lookup"><span data-stu-id="a7dec-103">You can suspend orchestration instances or ports from a query results list in the BizTalk Server Administration Console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a7dec-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="a7dec-104">Prerequisites</span></span>  
 <span data-ttu-id="a7dec-105">您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="a7dec-105">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-suspend-orchestration-instances-or-ports"></a><span data-ttu-id="a7dec-106">擱置協調流程執行個體或連接埠</span><span class="sxs-lookup"><span data-stu-id="a7dec-106">To suspend orchestration instances or ports</span></span>  
  
1.  <span data-ttu-id="a7dec-107">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="a7dec-107">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a7dec-108">在主控台樹狀目錄中，依序展開 **BizTalk Server 管理**, ，然後按一下 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="a7dec-108">In the console tree, expand **BizTalk Server Administration**, and then click the BizTalk group.</span></span>  
  
3.  <span data-ttu-id="a7dec-109">在詳細資料窗格中，按一下 [ **新查詢** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a7dec-109">In the details pane, click the **New Query** tab.</span></span>  
  
4.  <span data-ttu-id="a7dec-110">在 **查詢運算式** 群組 **值** 欄中，選取 **執行服務執行個體** 從下拉式清單方塊。</span><span class="sxs-lookup"><span data-stu-id="a7dec-110">In the **Query Expression** group, in the **Value** column, select **Running Service Instances** from the drop-down list box.</span></span>  
  
5.  <span data-ttu-id="a7dec-111">執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="a7dec-111">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="a7dec-112">暫止中的單一執行個體， **欄位名稱** 欄中的空白下拉式清單方塊旁邊的星號 (**\***)，請選取 **服務名稱** 篩選器，然後在 **值** 資料行中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="a7dec-112">To suspend a single instance, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select the **Service Name** filter and then in the **Value** column, specify the service name.</span></span>  
  
    -   <span data-ttu-id="a7dec-113">要擱置大量執行個體，在 **欄位名稱** 欄中的空白下拉式清單方塊旁邊的星號 (**\***)，請選取 **群組結果依據** ，然後在 **值** 資料行中，指定服務名稱。</span><span class="sxs-lookup"><span data-stu-id="a7dec-113">To suspend instances in bulk, in the **Field Name** column, in the empty drop-down list box next to the asterisk (**\***), select **Group Results By** and then in the **Value** column, specify the service name.</span></span>  
  
6.  <span data-ttu-id="a7dec-114">按一下  **執行查詢**。</span><span class="sxs-lookup"><span data-stu-id="a7dec-114">Click **Run Query**.</span></span>  
  
7.  <span data-ttu-id="a7dec-115">在查詢結果清單中，以滑鼠右鍵按一下您想要暫停，然後按一下 使用中的協調流程或連接埠 **擱置執行個體** 或 **擱置執行個體**。</span><span class="sxs-lookup"><span data-stu-id="a7dec-115">In the query results list, right-click the active orchestration or port you want to suspend, and then click **Suspend Instance** or **Suspend Instances**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7dec-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7dec-116">See Also</span></span>  
 [<span data-ttu-id="a7dec-117">調查協調流程、連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="a7dec-117">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)