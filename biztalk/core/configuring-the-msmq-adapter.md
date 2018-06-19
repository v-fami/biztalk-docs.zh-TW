---
title: 設定 MSMQ 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, configuring
- configuring [MSMQ adapters]
ms.assetid: 8f873ee1-4eaa-43d2-948d-aecc406a0bfb
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74e2cac70171a22dad391addc81daa696e204fd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232950"
---
# <a name="configuring-the-msmq-adapter"></a><span data-ttu-id="d3d4f-102">設定 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="d3d4f-102">Configuring the MSMQ Adapter</span></span>
<span data-ttu-id="d3d4f-103">本節包含關於設定 MSMQ 配接器的資訊。</span><span class="sxs-lookup"><span data-stu-id="d3d4f-103">This section includes information about configuring the MSMQ adapter.</span></span> <span data-ttu-id="d3d4f-104">您可以為接收位置和傳送埠設定 MSMQ 配接器。</span><span class="sxs-lookup"><span data-stu-id="d3d4f-104">You can configure the MSMQ adapter for both receive locations and send ports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3d4f-105">若要清除屬性工作表中的某些欄位，例如**使用者名**和**密碼**，屬性名稱 （不是值），以滑鼠右鍵按一下，然後按一下**設為空值**。</span><span class="sxs-lookup"><span data-stu-id="d3d4f-105">To clear certain fields in the property sheet, such as **User Name** and **Password**, right-click the property name (not the value), and then click **Nullify**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3d4f-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3d4f-106">In This Section</span></span>  
  
-   [<span data-ttu-id="d3d4f-107">如何設定 MSMQ 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="d3d4f-107">How to Configure an MSMQ Receive Handler</span></span>](../core/how-to-configure-an-msmq-receive-handler.md)  
  
-   [<span data-ttu-id="d3d4f-108">如何設定 MSMQ 接收位置</span><span class="sxs-lookup"><span data-stu-id="d3d4f-108">How to Configure an MSMQ Receive Location</span></span>](../core/how-to-configure-an-msmq-receive-location.md)  
  
-   [<span data-ttu-id="d3d4f-109">如何設定 MSMQ 傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="d3d4f-109">How to Configure an MSMQ Send Handler</span></span>](../core/how-to-configure-an-msmq-send-handler.md)  
  
-   [<span data-ttu-id="d3d4f-110">如何設定 MSMQ 傳送埠</span><span class="sxs-lookup"><span data-stu-id="d3d4f-110">How to Configure an MSMQ Send Port</span></span>](../core/how-to-configure-an-msmq-send-port.md)  
  
-   [<span data-ttu-id="d3d4f-111">如何設定 MSMQ 傳送埠</span><span class="sxs-lookup"><span data-stu-id="d3d4f-111">How to Configure an MSMQ Send Port</span></span>](../core/how-to-configure-an-msmq-send-port.md)  
  
-   [<span data-ttu-id="d3d4f-112">如何管理多個接收位置使用 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="d3d4f-112">How to Manage Multiple Receive Locations Using the MSMQ Adapter</span></span>](../core/how-to-manage-multiple-receive-locations-using-the-msmq-adapter.md)  
  
-   [<span data-ttu-id="d3d4f-113">訊息佇列的佇列</span><span class="sxs-lookup"><span data-stu-id="d3d4f-113">Message Queuing Queues</span></span>](../core/message-queuing-queues.md)  
  
-   [<span data-ttu-id="d3d4f-114">最佳化 MSMQ 配接器效能</span><span class="sxs-lookup"><span data-stu-id="d3d4f-114">Optimizing Performance of the MSMQ Adapter</span></span>](../core/optimizing-performance-of-the-msmq-adapter.md)  
  
-   [<span data-ttu-id="d3d4f-115">傳送和接收大型訊息使用 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="d3d4f-115">Sending and Receiving Large Messages Using the MSMQ Adapter</span></span>](../core/sending-and-receiving-large-messages-using-the-msmq-adapter.md)