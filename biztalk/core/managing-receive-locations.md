---
title: "管理接收位置 |Microsoft 文件"
description: "使用在 BizTalk Server 中，包括建立、 變更內容、 啟用和停用、 新增憑證，以及刪除接收位置"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b3ff581-e7e9-4a6e-a9ea-70c55a3b9318
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ddaf0756eb2f0b78ddb851d13ff1acab12c6a83
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="manage-receive-locations"></a><span data-ttu-id="7671e-103">管理接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-103">Manage Receive Locations</span></span>

## <a name="overview"></a><span data-ttu-id="7671e-104">概觀</span><span class="sxs-lookup"><span data-stu-id="7671e-104">Overview</span></span>
<span data-ttu-id="7671e-105">本節提供有關使用 BizTalk Server 管理主控台來建立、設定和管理 BizTalk 應用程式之接收位置的指示。</span><span class="sxs-lookup"><span data-stu-id="7671e-105">This section provides instructions on creating, configuring, and managing receive locations for a BizTalk application by using the BizTalk Server Administration console.</span></span> <span data-ttu-id="7671e-106">接收位置包含輸入訊息送達的位址，以及處理在該位址所收到訊息的傳訊管線。</span><span class="sxs-lookup"><span data-stu-id="7671e-106">A receive location consists of an address at which inbound messages arrive and the messaging pipeline that processes the message received at that address.</span></span> <span data-ttu-id="7671e-107">如需背景資訊，請參閱[接收位置](../core/receive-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="7671e-107">For background information, see [Receive Locations](../core/receive-locations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7671e-108">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7671e-108">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="7671e-109">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="7671e-109">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 
  
## <a name="next-steps"></a><span data-ttu-id="7671e-110">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="7671e-110">Next steps</span></span> 
  
-   [<span data-ttu-id="7671e-111">建立接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-111">Create a Receive Location</span></span>](../core/how-to-create-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-112">編輯屬性的接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-112">Edit the Properties of a Receive Location</span></span>](../core/how-to-edit-the-properties-of-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-113">設定每個執行個體管線屬性的接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-113">Configure Per-instance Pipeline Properties for a Receive Location</span></span>](../core/how-to-configure-per-instance-pipeline-properties-for-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-114">啟用接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-114">Enable a Receive Location</span></span>](../core/how-to-enable-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-115">停用接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-115">Disable a Receive Location</span></span>](../core/how-to-disable-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-116">設定排程的接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-116">Configure Scheduling for a Receive Location</span></span>](../core/how-to-configure-scheduling-for-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-117">憑證指派給接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-117">Assign a Certificate to a Receive Location</span></span>](../core/how-to-assign-a-certificate-to-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-118">移除憑證，以從接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-118">Remove a Certificate from a Receive Location</span></span>](../core/how-to-remove-a-certificate-from-a-receive-location.md)  
  
-   [<span data-ttu-id="7671e-119">刪除接收位置</span><span class="sxs-lookup"><span data-stu-id="7671e-119">Delete a Receive Location</span></span>](../core/how-to-delete-a-receive-location.md)