---
title: 升級至 BizTalk Server 2013 和 2013 R2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- upgrading, BizTalk Server
- deploying [BizTalk Server], upgrading
- BizTalk Server, upgrading
- upgrading
ms.assetid: acb0a96e-091b-45c3-8d41-affe9ffcf134
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 97337438ca6be06b542baf61ad8d26fa2045180a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22300030"
---
# <a name="upgrade-to-biztalk-server-2013-and-2013-r2"></a><span data-ttu-id="26298-102">升級至 BizTalk Server 2013 及 2013 R2</span><span class="sxs-lookup"><span data-stu-id="26298-102">Upgrade to BizTalk Server 2013 and 2013 R2</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="26298-103"> 的設計目的是提供從舊版輕鬆升級的經驗。</span><span class="sxs-lookup"><span data-stu-id="26298-103"> is designed to allow for an easy upgrade experience from previous versions.</span></span> <span data-ttu-id="26298-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013 及 2013 R2 升級指南位於 [BizTalk Server 2013 相關的安裝指南](http://www.microsoft.com/download/details.aspx?id=35552)。</span><span class="sxs-lookup"><span data-stu-id="26298-104">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2013 and 2013 R2 Upgrade Guide is available at [Installation Guides Related to BizTalk Server 2013](http://www.microsoft.com/download/details.aspx?id=35552).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26298-105">執行升級時，會取代結構描述的壓縮檔。</span><span class="sxs-lookup"><span data-stu-id="26298-105">The compressed file of schemas will be replaced when an upgrade is performed.</span></span> <span data-ttu-id="26298-106">如果您將 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 升級至更新的組建 (例如，從測試版升級至零售版)，原來安裝中的 MicrosoftEdiXSDTemplates.exe 檔案會遭取代為與升級相關聯的 MicrosoftEdiXSDTemplates.exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="26298-106">If you upgrade Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to a later build (for example, from a beta version to the retail release version), the MicrosoftEdiXSDTemplates.exe file in your installation will be replaced with the MicrosoftEdiXSDTemplates.exe file associated with the upgrade.</span></span> <span data-ttu-id="26298-107">如果您打算繼續使用舊壓縮檔中的結構描述，除非備份舊壓縮檔，否則您在升級後將無法再存取這些壓縮檔。</span><span class="sxs-lookup"><span data-stu-id="26298-107">If you plan to continue to use the schemas from the old compressed file, you will no longer have access to the compressed file after the upgrade unless you back up the old compressed file.</span></span> <span data-ttu-id="26298-108">如需詳細資訊，請參閱**安裝 EDI 結構描述**在[後設定步驟來最佳化您的環境](post-configuration-steps-to-optimize-your-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="26298-108">For more information, see **Install EDI schemas** at [Post-configuration steps to optimize your environment](post-configuration-steps-to-optimize-your-environment.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26298-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26298-109">See Also</span></span>  
[<span data-ttu-id="26298-110">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="26298-110">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)