---
title: 設定來源系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 722dd52c-1eea-453c-9a36-9b8d9cf19350
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73f5d785c20d1390ae811d737e9169951e0270e7
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26009303"
---
# <a name="configuring-the-source-system"></a><span data-ttu-id="42528-102">設定來源系統</span><span class="sxs-lookup"><span data-stu-id="42528-102">Configuring the Source System</span></span>
<span data-ttu-id="42528-103">基於 BizTalk Server 記錄傳送，並不重要如果來源系統位於單一[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，或如果它會分散於多個執行個體裝載於 Windows Server 叢集。</span><span class="sxs-lookup"><span data-stu-id="42528-103">For the purposes of BizTalk Server log shipping, it does not matter if the source system is located on a single [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance or if it is distributed among multiple instances hosted in a Windows Server cluster.</span></span> <span data-ttu-id="42528-104">沒有以外成功執行 「 備份 BizTalk Server 」 工作所需的其他考量。</span><span class="sxs-lookup"><span data-stu-id="42528-104">There are no additional considerations other than those required to successfully run the Backup BizTalk Server job.</span></span> <span data-ttu-id="42528-105">若要設定此作業時，請參閱[如何設定 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkID=154072)(http://go.microsoft.com/fwlink/?LinkID=154072) 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="42528-105">To configure this job, see [How to Configure the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkID=154072) (http://go.microsoft.com/fwlink/?LinkID=154072) in BizTalk Server Help.</span></span> <span data-ttu-id="42528-106">您已設定 「 備份 BizTalk Server 」 工作之後，繼續進行本主題[如何設定目的系統](../technical-guides/how-to-configure-the-destination-system.md)。</span><span class="sxs-lookup"><span data-stu-id="42528-106">After you have configured the Backup BizTalk Server Job, proceed to the topic [How to Configure the Destination System](../technical-guides/how-to-configure-the-destination-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42528-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="42528-107">See Also</span></span>  
 [<span data-ttu-id="42528-108">設定 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="42528-108">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)