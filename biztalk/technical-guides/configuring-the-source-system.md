---
title: 設定來源系統 |Microsoft Docs
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
ms.openlocfilehash: 87cf66470ff2d05f4446fbcb81eb2a533064d3f6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024364"
---
# <a name="configuring-the-source-system"></a><span data-ttu-id="069e3-102">設定來源系統</span><span class="sxs-lookup"><span data-stu-id="069e3-102">Configuring the Source System</span></span>
<span data-ttu-id="069e3-103">基於 BizTalk Server 記錄傳送的目的，它並不重要如果來源系統位於單一[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]執行個體，或如果它分散裝載於 Windows Server 叢集中的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="069e3-103">For the purposes of BizTalk Server log shipping, it does not matter if the source system is located on a single [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance or if it is distributed among multiple instances hosted in a Windows Server cluster.</span></span> <span data-ttu-id="069e3-104">沒有任何額外的考量以外，才能成功執行 「 備份 BizTalk Server 」 工作。</span><span class="sxs-lookup"><span data-stu-id="069e3-104">There are no additional considerations other than those required to successfully run the Backup BizTalk Server job.</span></span> <span data-ttu-id="069e3-105">若要設定這項作業，請參閱[如何設定 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkID=154072)(<http://go.microsoft.com/fwlink/?LinkID=154072>) 在 BizTalk Server 說明中。</span><span class="sxs-lookup"><span data-stu-id="069e3-105">To configure this job, see [How to Configure the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkID=154072) (<http://go.microsoft.com/fwlink/?LinkID=154072>) in BizTalk Server Help.</span></span> <span data-ttu-id="069e3-106">您已設定 「 備份 BizTalk Server 」 工作之後，繼續進行本主題[如何設定目的系統](../technical-guides/how-to-configure-the-destination-system.md)。</span><span class="sxs-lookup"><span data-stu-id="069e3-106">After you have configured the Backup BizTalk Server Job, proceed to the topic [How to Configure the Destination System](../technical-guides/how-to-configure-the-destination-system.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="069e3-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="069e3-107">See Also</span></span>  
 [<span data-ttu-id="069e3-108">設定 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="069e3-108">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)