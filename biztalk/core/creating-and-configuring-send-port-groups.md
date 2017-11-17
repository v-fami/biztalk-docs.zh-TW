---
title: "建立和設定傳送埠群組 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6dd1ac37-a6e4-4ea0-9eff-ee400b3f3d74
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 987b1e9fe780ad6841a13a477678d3b61556fac7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-configuring-send-port-groups"></a><span data-ttu-id="f8e69-102">建立和設定傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="f8e69-102">Creating and Configuring Send Port Groups</span></span>

## <a name="overview"></a><span data-ttu-id="f8e69-103">概觀</span><span class="sxs-lookup"><span data-stu-id="f8e69-103">Overview</span></span>
<span data-ttu-id="f8e69-104">本節提供使用 BizTalk Server 管理主控台將傳送埠群組新增到 BizTalk 應用程式以及設定和刪除傳送埠群組的指示。</span><span class="sxs-lookup"><span data-stu-id="f8e69-104">This section provides instructions on using the BizTalk Server Administration console to add send port groups to a BizTalk application as well as to configure and delete send port groups.</span></span> <span data-ttu-id="f8e69-105">傳送埠群組是傳送埠的命名集合，可用來將相同的訊息傳送到多個目的地。</span><span class="sxs-lookup"><span data-stu-id="f8e69-105">A send port group is a named collection of send ports that can be used to send the same message to multiple destinations.</span></span> <span data-ttu-id="f8e69-106">您可以將傳送埠群組繫結至協調流程連接埠，或是同單一傳送埠一樣，在以內容為基礎的路由選擇 (CBR) 中使用它們。</span><span class="sxs-lookup"><span data-stu-id="f8e69-106">You can bind send port groups to orchestration ports or use them for content-based routing (CBR) just as you can for a single send port.</span></span> <span data-ttu-id="f8e69-107">如需傳送埠群組的背景資訊，請參閱[傳送埠與傳送埠群組](../core/send-ports-and-send-port-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="f8e69-107">For background information on send port groups, see [Send Ports and Send Port Groups](../core/send-ports-and-send-port-groups.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8e69-108">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="f8e69-108">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="f8e69-109">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="f8e69-109">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="f8e69-110">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="f8e69-110">Next steps</span></span>
  
-   [<span data-ttu-id="f8e69-111">建立傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="f8e69-111">Create a Send Port Group</span></span>](../core/how-to-create-a-send-port-group.md)  
  
-   [<span data-ttu-id="f8e69-112">新增傳送埠至傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="f8e69-112">Add a Send Port to a Send Port Group</span></span>](../core/how-to-add-a-send-port-to-a-send-port-group.md)  
  
-   [<span data-ttu-id="f8e69-113">從傳送埠群組移除傳送埠</span><span class="sxs-lookup"><span data-stu-id="f8e69-113">Remove a Send Port from a Send Port Group</span></span>](../core/how-to-remove-a-send-port-from-a-send-port-group.md)  
  
-   [<span data-ttu-id="f8e69-114">設定傳送埠群組篩選</span><span class="sxs-lookup"><span data-stu-id="f8e69-114">Configure Filters for a Send Port Group</span></span>](../core/how-to-configure-filters-for-a-send-port-group.md)  
  
-   [<span data-ttu-id="f8e69-115">刪除傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="f8e69-115">Delete a Send Port Group</span></span>](../core/how-to-delete-a-send-port-group.md)