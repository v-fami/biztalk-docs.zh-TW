---
title: 轉換，並將訊息路由至磁碟資料夾、 佇列或 FTP 資料夾 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5bfdbc38-6663-4d95-a0ed-57fec0245b9f
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dcbc9d42fbed5dfd73aee910ba2e1a40da595658
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009839"
---
# <a name="transforming-and-routing-a-message-to-disk-folder-queue-or-ftp-folder"></a><span data-ttu-id="98457-102">轉換，並將訊息路由至磁碟資料夾、 佇列或 FTP 資料夾</span><span class="sxs-lookup"><span data-stu-id="98457-102">Transforming and Routing a Message to Disk Folder, Queue, or FTP Folder</span></span>
<span data-ttu-id="98457-103">在此使用案例中，ESB 轉換提交透過路線 Web 服務或任何上手的訊息。</span><span class="sxs-lookup"><span data-stu-id="98457-103">In this use case, the ESB transforms a message submitted through the Itinerary Web service or any on-ramp.</span></span> <span data-ttu-id="98457-104">動態解析查閱是 FILE 類型、 FTP 或佇列位置決定地圖名稱 （轉換） 以及訊息的目標端點，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="98457-104">A dynamic resolution lookup of type FILE, FTP, or queue location determines the map name (for transformation) and the target endpoint for the message, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="98457-105">![轉換磁碟資料夾](../esb-toolkit/media/ch3-transformingdiskfolder.gif "Ch3 TransformingDiskFolder")</span><span class="sxs-lookup"><span data-stu-id="98457-105">![Transforming Disk Folder](../esb-toolkit/media/ch3-transformingdiskfolder.gif "Ch3-TransformingDiskFolder")</span></span>  
  
 <span data-ttu-id="98457-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="98457-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="98457-107">**轉換，並將訊息路由至磁碟資料夾**</span><span class="sxs-lookup"><span data-stu-id="98457-107">**Transforming and routing a message to a disk folder**</span></span>  
  
 <span data-ttu-id="98457-108">動態解析 」 範例隨附[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]示範這個使用案例。</span><span class="sxs-lookup"><span data-stu-id="98457-108">The Dynamic Resolution sample included with [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="98457-109">它會顯示如何以動態解析端點位置、 設定路由的屬性，並解析以及執行 BizTalk Server 對應，在訊息層級，而不需使用協調流程中使用的元件。</span><span class="sxs-lookup"><span data-stu-id="98457-109">It shows how to use the components to dynamically resolve endpoint location, set routing properties, and resolve and execute BizTalk Server maps at the messaging level, without using an orchestration.</span></span> <span data-ttu-id="98457-110">它也示範單向和雙向的訊息模式。</span><span class="sxs-lookup"><span data-stu-id="98457-110">It also demonstrates both one-way and two-way messaging patterns.</span></span>  
  
 <span data-ttu-id="98457-111">此使用案例的延伸模組是轉換的簡單的路由解決方案將內送訊息路由至檔案、 FTP 或沒有其他步驟的佇列位置。</span><span class="sxs-lookup"><span data-stu-id="98457-111">An extension of this use case is a simple routing solution that routes an incoming message to a file, FTP, or queue location without the additional step of transformation.</span></span>  
  
 <span data-ttu-id="98457-112">如需詳細資訊，請參閱[安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="98457-112">For more information, see [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md).</span></span>