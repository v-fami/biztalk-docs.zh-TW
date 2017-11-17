---
title: "設定 BizTalk 記錄傳送的其他資料庫 |Microsoft 文件"
description: "加入自訂的資料庫備份 BizTalk Server 」 工作，以及 BizTalk Server 中的記錄傳送"
ms.custom: 
ms.date: 11/01/2017
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
ms.openlocfilehash: 1f4eb0b690f81b16d739183633c6507b2ad87226
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="configuring-biztalk-server-log-shipping-for-additional-databases"></a><span data-ttu-id="5464d-103">設定 BizTalk Server 記錄傳送的其他資料庫</span><span class="sxs-lookup"><span data-stu-id="5464d-103">Configuring BizTalk Server Log Shipping for Additional Databases</span></span>

## <a name="overview"></a><span data-ttu-id="5464d-104">概觀</span><span class="sxs-lookup"><span data-stu-id="5464d-104">Overview</span></span>
<span data-ttu-id="5464d-105">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，新增至 「 備份 BizTalk Server 」 工作的工作會自動加入至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="5464d-105">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], jobs added to the Backup BizTalk Server job are automatically added to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping.</span></span> <span data-ttu-id="5464d-106">您不需要採取額外步驟來設定新的資料庫加入至 「 備份 BizTalk Server 」 工作的記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="5464d-106">You do not have to take additional steps to configure log shipping for new databases added to the Backup BizTalk Server job.</span></span> <span data-ttu-id="5464d-107">不過，請務必要將自訂資料庫加入視情況\<OtherDatabases > SampleUpdateInfo.xml 檔案的區段。</span><span class="sxs-lookup"><span data-stu-id="5464d-107">However, be sure to add custom databases as appropriate under the \<OtherDatabases> section of the SampleUpdateInfo.xml file.</span></span> <span data-ttu-id="5464d-108">[設定記錄傳送的目的系統](../core/how-to-configure-the-destination-system-for-log-shipping.md)和[備份自訂資料庫](../core/how-to-back-up-custom-databases.md)提供一些指引。</span><span class="sxs-lookup"><span data-stu-id="5464d-108">[Configure the Destination System for Log Shipping](../core/how-to-configure-the-destination-system-for-log-shipping.md) and [Back Up Custom Databases](../core/how-to-back-up-custom-databases.md) provides some guidance.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5464d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5464d-109">See Also</span></span>  
 [<span data-ttu-id="5464d-110">設定 BizTalk Server 記錄傳送</span><span class="sxs-lookup"><span data-stu-id="5464d-110">Configuring BizTalk Server Log Shipping</span></span>](../technical-guides/configuring-biztalk-server-log-shipping.md)