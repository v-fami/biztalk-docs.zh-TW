---
title: 準備進行災害復原的應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ef93099-aa6b-424a-a4ce-87d855c6afe3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7028b1386f71f653dfc41b9de2522cdbd8d02126
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302334"
---
# <a name="preparing-applications-for-disaster-recovery"></a><span data-ttu-id="9d850-102">準備進行災害復原的應用程式</span><span class="sxs-lookup"><span data-stu-id="9d850-102">Preparing Applications for Disaster Recovery</span></span>
<span data-ttu-id="9d850-103">BizTalk 應用程式 （二進位檔和設定成品例如接收位置和傳送埠） 會部署到生產環境 BizTalk 群組中，當群組在災害復原站台上還原。</span><span class="sxs-lookup"><span data-stu-id="9d850-103">BizTalk applications (binaries and configuration artifacts such as receive locations and send ports) are deployed to the production BizTalk group when the group is restored at the disaster recovery site.</span></span> <span data-ttu-id="9d850-104">此設定可能要改變取決於是否有設定位置例如接收位置和傳送實際執行環境專屬的連接埠。</span><span class="sxs-lookup"><span data-stu-id="9d850-104">This configuration may have to be altered depending on whether there are configuration locations such as receive locations and send ports that are production-specific.</span></span>  
  
 <span data-ttu-id="9d850-105">為加速還原的應用程式在災害復原站台， [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi 檔案安裝二進位檔上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段伺服器必須保持最新的災害復原[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="9d850-105">To speed the restoration of applications at the disaster recovery site, a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi file that installs the binaries on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers must be kept up-to-date on the disaster recovery [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers.</span></span> <span data-ttu-id="9d850-106">在災害復原站台還原的實際執行的 BizTalk 群組時，可能需要災害復原特定應用程式組態.msi 檔案安裝，才能設定應用程式災害復原特定成品，例如接收位置和傳送埠，視。</span><span class="sxs-lookup"><span data-stu-id="9d850-106">When the production BizTalk group is restored at the disaster recovery site, a disaster recovery-specific application configuration .msi file may need to be installed in order to configure the application for disaster recovery-specific artifacts, such as receive locations and send ports, as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d850-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d850-107">See Also</span></span>  
 [<span data-ttu-id="9d850-108">部署應用程式</span><span class="sxs-lookup"><span data-stu-id="9d850-108">Deploying an Application</span></span>](../technical-guides/deploying-an-application.md)