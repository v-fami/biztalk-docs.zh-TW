---
title: "建立及設定的快速連結傳送埠 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b26ed07-b7ed-48a5-9bd9-dfba9c1d3c02
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31361c9a6dff1d35c21bede4a82d513c6a073218
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-configuring-send-ports"></a><span data-ttu-id="96910-102">建立和設定傳送埠</span><span class="sxs-lookup"><span data-stu-id="96910-102">Creating and Configuring Send Ports</span></span>

## <a name="overview"></a><span data-ttu-id="96910-103">概觀</span><span class="sxs-lookup"><span data-stu-id="96910-103">Overview</span></span>
<span data-ttu-id="96910-104">本節提供關於使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台來建立和設定 BizTalk 應用程式之傳送埠的指示。</span><span class="sxs-lookup"><span data-stu-id="96910-104">This section provides instructions on using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to create and configure send ports for a BizTalk application.</span></span> <span data-ttu-id="96910-105">傳送埠是傳送訊息或接收訊息的目的或來源位置，並會以其唯一的名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="96910-105">A send port is a location to which messages are sent or from which messages are received and is uniquely identified by its name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96910-106">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="96910-106">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="96910-107">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="96910-107">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="96910-108">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="96910-108">Next steps</span></span>
  
-   [<span data-ttu-id="96910-109">建立傳送埠</span><span class="sxs-lookup"><span data-stu-id="96910-109">Create a Send Port</span></span>](../core/how-to-create-a-send-port2.md)  
  
-   [<span data-ttu-id="96910-110">檢視的傳送埠的執行個體資訊</span><span class="sxs-lookup"><span data-stu-id="96910-110">View Instance Information for a Send Port</span></span>](../core/how-to-view-instance-information-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-111">設定傳送埠的每個執行個體管線屬性</span><span class="sxs-lookup"><span data-stu-id="96910-111">Configure Per-Instance Pipeline Properties for a Send Port</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-112">新增傳送埠至傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="96910-112">Add a Send Port to a Send Port Group</span></span>](../core/how-to-add-a-send-port-to-a-send-port-group.md)  
  
-   [<span data-ttu-id="96910-113">從傳送埠群組移除傳送埠</span><span class="sxs-lookup"><span data-stu-id="96910-113">Remove a Send Port from a Send Port Group</span></span>](../core/how-to-remove-a-send-port-from-a-send-port-group.md)  
  
-   [<span data-ttu-id="96910-114">設定傳送埠的傳輸進階選項</span><span class="sxs-lookup"><span data-stu-id="96910-114">Configure Transport Advanced Options for a Send Port</span></span>](../core/how-to-configure-transport-advanced-options-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-115">設定傳送埠備份傳輸選項</span><span class="sxs-lookup"><span data-stu-id="96910-115">Configure Backup Transport Options for a Send Port</span></span>](../core/how-to-configure-backup-transport-options-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-116">設定傳送埠的輸入的對應</span><span class="sxs-lookup"><span data-stu-id="96910-116">Configure Inbound Maps for a Send Port</span></span>](../core/how-to-configure-inbound-maps-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-117">設定傳送埠的輸出對應</span><span class="sxs-lookup"><span data-stu-id="96910-117">Configure Outbound Maps for a Send Port</span></span>](../core/how-to-configure-outbound-maps-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-118">設定傳送埠的篩選</span><span class="sxs-lookup"><span data-stu-id="96910-118">Configure Filters for a Send Port</span></span>](../core/how-to-configure-filters-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-119">指派憑證給傳送埠</span><span class="sxs-lookup"><span data-stu-id="96910-119">Assign a Certificate to a Send Port</span></span>](../core/how-to-assign-a-certificate-to-a-send-port.md)  
  
-   [<span data-ttu-id="96910-120">從傳送埠移除憑證</span><span class="sxs-lookup"><span data-stu-id="96910-120">Remove a Certificate from a Send Port</span></span>](../core/how-to-remove-a-certificate-from-a-send-port.md)  
  
-   [<span data-ttu-id="96910-121">設定傳送埠的追蹤</span><span class="sxs-lookup"><span data-stu-id="96910-121">Configure Tracking for a Send Port</span></span>](../core/how-to-configure-tracking-for-a-send-port.md)  
  
-   [<span data-ttu-id="96910-122">刪除傳送埠</span><span class="sxs-lookup"><span data-stu-id="96910-122">Delete a Send Port</span></span>](../core/how-to-delete-a-send-port.md)