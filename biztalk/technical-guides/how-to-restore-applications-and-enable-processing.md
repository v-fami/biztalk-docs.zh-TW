---
title: 如何還原應用程式，並啟用處理 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 83144965-a51a-481a-afd6-7f573b69badb
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aae2a6d9b4f3a35c55ffa731323547b1b54a4d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36999407"
---
# <a name="how-to-restore-applications-and-enable-processing"></a><span data-ttu-id="307cf-102">如何還原應用程式，並啟用處理</span><span class="sxs-lookup"><span data-stu-id="307cf-102">How to Restore Applications and Enable Processing</span></span>
<span data-ttu-id="307cf-103">設定 BizTalk 群組中的應用程式，並啟用主題所述的步驟之後的應用程式處理[如何更新執行階段電腦](../technical-guides/how-to-update-the-runtime-computers.md)。</span><span class="sxs-lookup"><span data-stu-id="307cf-103">Configure the applications in the BizTalk group and enable application processing after following the steps described in the topic [How to Update the Runtime Computers](../technical-guides/how-to-update-the-runtime-computers.md).</span></span>  
  
### <a name="to-enable-application-configuration-and-restore-application-processing"></a><span data-ttu-id="307cf-104">若要啟用應用程式組態，並還原應用程式處理</span><span class="sxs-lookup"><span data-stu-id="307cf-104">To enable application configuration and restore application processing</span></span>  
  
1. <span data-ttu-id="307cf-105">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組中每個 BizTalk 伺服器上的應用程式安裝 MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="307cf-105">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Installation MSI file on each BizTalk server in the group.</span></span>  
  
2. <span data-ttu-id="307cf-106">執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定災害復原站台的應用程式群組中的一部伺服器上的應用程式設定 MSI 檔案。</span><span class="sxs-lookup"><span data-stu-id="307cf-106">Run the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Configuration MSI file on one server in the group to configure the application for the disaster recovery site.</span></span> <span data-ttu-id="307cf-107">接收位置的名稱，並傳送連接埠保持不變。</span><span class="sxs-lookup"><span data-stu-id="307cf-107">The names for receive locations and send ports remain the same.</span></span> <span data-ttu-id="307cf-108">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使這些成品會指向正確的位置，嚴重損壞修復環境中，應用程式設定 MSI 檔案會更新繫結。</span><span class="sxs-lookup"><span data-stu-id="307cf-108">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Application Configuration MSI file updates bindings so that these artifacts point to the correct locations in the disaster recovery environment.</span></span>  
  
   > [!NOTE]  
   >  <span data-ttu-id="307cf-109">如果接收位置和傳送埠不會影響生產網站遺失，它可能不需要重新設定應用程式的災害復原具體的位置。</span><span class="sxs-lookup"><span data-stu-id="307cf-109">If receive locations and send ports are not affected by the loss of the production site, it may not be necessary to reconfigure the application with disaster recovery-specific locations.</span></span>  
  
3. <span data-ttu-id="307cf-110">還原應用程式處理，讓所有的應用程式接收位置、 傳送埠，以及主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="307cf-110">Restore application processing by enabling all application receive locations, send ports, and host instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307cf-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="307cf-111">See Also</span></span>  
 [<span data-ttu-id="307cf-112">復原執行階段電腦</span><span class="sxs-lookup"><span data-stu-id="307cf-112">Recovering the Runtime Computers</span></span>](../technical-guides/recovering-the-runtime-computers.md)