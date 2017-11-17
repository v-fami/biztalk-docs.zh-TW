---
title: "使用指令碼來部署應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e683c5f-7576-4382-9952-d577cd00186c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4566a810489a9f6c46424a525908aa5a2fbb6bee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-scripts-to-deploy-applications"></a><span data-ttu-id="cb507-102">使用指令碼來部署應用程式</span><span class="sxs-lookup"><span data-stu-id="cb507-102">Using Scripts to Deploy Applications</span></span>
<span data-ttu-id="cb507-103">部署 BizTalk 應用程式，可能的話，您應該使用指令碼。</span><span class="sxs-lookup"><span data-stu-id="cb507-103">You should use scripts to deploy BizTalk applications where possible.</span></span> <span data-ttu-id="cb507-104">指令碼部署程序期間減少人為錯誤的風險。</span><span class="sxs-lookup"><span data-stu-id="cb507-104">Scripting reduces the risk of human error during the deployment process.</span></span> <span data-ttu-id="cb507-105">您也應該記錄深度您部署程序。</span><span class="sxs-lookup"><span data-stu-id="cb507-105">You should also document your deployment procedures in depth.</span></span> <span data-ttu-id="cb507-106">您應該記錄任何您不要的指令碼非常詳細的步驟。</span><span class="sxs-lookup"><span data-stu-id="cb507-106">You should document anything that you do not script with very detailed steps.</span></span> <span data-ttu-id="cb507-107">這包括記錄到外部系統和非 Microsoft 元件部署的任何變更。</span><span class="sxs-lookup"><span data-stu-id="cb507-107">This includes documenting any changes to external systems and to deployment of non-Microsoft components.</span></span>  
  
## <a name="using-btstask"></a><span data-ttu-id="cb507-108">使用 BTSTask</span><span class="sxs-lookup"><span data-stu-id="cb507-108">Using BTSTask</span></span>  
 <span data-ttu-id="cb507-109">您可以建立 BizTalk 應用程式，以及有關匯入現有的指令碼使用 BTSTask.exe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi 封裝。</span><span class="sxs-lookup"><span data-stu-id="cb507-109">You can use BTSTask.exe to script the creation of BizTalk applications, as well as to import existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] .msi packages.</span></span> <span data-ttu-id="cb507-110">如果應用程式的建立已編寫指令碼，然後封裝能夠自動建置組建伺服器上使用自動化程序。</span><span class="sxs-lookup"><span data-stu-id="cb507-110">If the creation of the applications is scripted, then the packages can be automatically built using an automated process on a build server.</span></span>  
  
 <span data-ttu-id="cb507-111">請參閱下列主題中關於指令碼的 BizTalk 應用程式部署的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="cb507-111">See the following topics for more information about scripting BizTalk application deployments:</span></span>  
  
-   <span data-ttu-id="cb507-112">[部署和管理 BizTalk 應用程式](http://go.microsoft.com/fwlink/?LinkId=154210)(http://go.microsoft.com/fwlink/?LinkId=154210)</span><span class="sxs-lookup"><span data-stu-id="cb507-112">[Deploying and Managing BizTalk Applications](http://go.microsoft.com/fwlink/?LinkId=154210) (http://go.microsoft.com/fwlink/?LinkId=154210)</span></span>  
  
-   <span data-ttu-id="cb507-113">[了解 BizTalk Server 應用程式部署](http://go.microsoft.com/fwlink/?LinkId=101599)(http://go.microsoft.com/fwlink/?LinkId=101599)</span><span class="sxs-lookup"><span data-stu-id="cb507-113">[Understanding BizTalk Server Application Deployment](http://go.microsoft.com/fwlink/?LinkId=101599) (http://go.microsoft.com/fwlink/?LinkId=101599)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="cb507-114">此第二個文件也適用於[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cb507-114">This latter article also applies to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb507-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb507-115">See Also</span></span>  
 [<span data-ttu-id="cb507-116">檢查清單： 設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cb507-116">Checklist: Configuring BizTalk Server</span></span>](../technical-guides/checklist-configuring-biztalk-server.md)