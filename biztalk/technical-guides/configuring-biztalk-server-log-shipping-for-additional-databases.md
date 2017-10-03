---
title: "設定 BizTalk Server 記錄傳送的其他資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fc2ae67-5cb9-4d53-9bf7-c88f84914960
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b16b1d262b07ecaa62e87456f10bece225b3b34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a><span data-ttu-id="65bd6-102">設定 BizTalk Server 記錄傳送的其他資料庫</span><span class="sxs-lookup"><span data-stu-id="65bd6-102">Configuring BizTalk Server Log Shipping for Additional Databases</span></span>
<span data-ttu-id="65bd6-103">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，新增至 「 備份 BizTalk Server 」 工作的工作會自動加入至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="65bd6-103">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], jobs added to the Backup BizTalk Server job are automatically added to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping.</span></span> <span data-ttu-id="65bd6-104">您不需要採取額外步驟來設定新的資料庫加入至 「 備份 BizTalk Server 」 工作的記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="65bd6-104">You do not have to take additional steps to configure log shipping for new databases added to the Backup BizTalk Server job.</span></span> <span data-ttu-id="65bd6-105">不過，請務必要將自訂資料庫加入視情況\<OtherDatabases > 22 的步驟中所述的 SampleUpdateInfo.xml 檔案的區段[如何設定記錄傳送目的地系統](http://go.microsoft.com/fwlink/?LinkId=151402)(http: / / go.microsoft.com/fwlink/ 嗎？LinkId = 151402) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="65bd6-105">However, be sure to add custom databases as appropriate under the \<OtherDatabases> section of the SampleUpdateInfo.xml file as described in step 22 of [How to Configure the Destination System for Log Shipping](http://go.microsoft.com/fwlink/?LinkId=151402) (http://go.microsoft.com/fwlink/?LinkId=151402) in [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65bd6-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65bd6-106">See Also</span></span>  
 [<span data-ttu-id="65bd6-107">設定 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="65bd6-107">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)