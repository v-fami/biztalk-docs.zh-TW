---
title: "備份 BizTalk Server 應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b51e3ae6-08ed-48ca-8977-13f46144a5fa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d125a1430aa2d044abba7632fa31a9c89f2bc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-biztalk-server-applications"></a><span data-ttu-id="242e6-102">備份 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="242e6-102">Backing Up BizTalk Server Applications</span></span>
<span data-ttu-id="242e6-103">若要確保硬體失敗後可以復原您的 BizTalk Server 系統，擁有良好的備份是很重要的。</span><span class="sxs-lookup"><span data-stu-id="242e6-103">To ensure that you can recover your BizTalk Server system after a hardware failure, it is important to have good backups.</span></span> <span data-ttu-id="242e6-104">在備份過程中，您可以匯出 BizTalk 應用程式到遠端伺服器以及備份這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="242e6-104">As a part of keeping backups, it is a good idea to export your BizTalk applications to a remote server and to back up these applications.</span></span>  
  
 <span data-ttu-id="242e6-105">之後，在還原 BizTalk Server 資料庫及重新安裝 BizTalk Server 時，您就可以匯入這些應用程式。</span><span class="sxs-lookup"><span data-stu-id="242e6-105">Later, when you restore the BizTalk Server databases and reinstall BizTalk Server, you can import these applications.</span></span> <span data-ttu-id="242e6-106">如需如何匯出和匯入應用程式的詳細資訊，請參閱[部署和管理 BizTalk 應用程式](../core/deploying-and-managing-biztalk-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="242e6-106">For more information about how to export and import applications, see [Deploying and Managing BizTalk Applications](../core/deploying-and-managing-biztalk-applications.md).</span></span>  
  
 <span data-ttu-id="242e6-107">對於所有部署在電腦上的 BizTalk 應用程式，您應匯出 .msi 檔案，並將其儲存在備份位置 (不同的伺服器上)。</span><span class="sxs-lookup"><span data-stu-id="242e6-107">For all BizTalk applications deployed on the computer, you should export the .msi files and save them in your backup location (on a different server).</span></span> <span data-ttu-id="242e6-108">.msi 檔案可讓您在復原目的電腦後重新安裝 BizTalk Server 所需的資源。</span><span class="sxs-lookup"><span data-stu-id="242e6-108">The .msi files enable you to reinstall the resources required by BizTalk Server after you recover the destination computer.</span></span> <span data-ttu-id="242e6-109">您應確定 .msi 檔案包含所有必要的資源，以及指定在 .msi 安裝上要對這些資源執行的動作。</span><span class="sxs-lookup"><span data-stu-id="242e6-109">You should ensure that the .msi files include all of the required resources, and that you specify the actions to be performed on the .msi installation for these resources.</span></span> <span data-ttu-id="242e6-110">如果您的 BizTalk 應用程式相依於未包含在 .msi 檔案中的任何使用者組件或其他 DLL，就必須分別將其備份。</span><span class="sxs-lookup"><span data-stu-id="242e6-110">If your BizTalk application depends on any user assemblies or other DLLs that are not included in the .msi files, you must back up them up separately.</span></span>  
  
 <span data-ttu-id="242e6-111">對以內容為基礎的路由實例以及具有協調流程的實例，應用程式匯出程序都相同。</span><span class="sxs-lookup"><span data-stu-id="242e6-111">The application export process is the same for content-based routing scenarios as well as scenarios that have orchestrations.</span></span> <span data-ttu-id="242e6-112">只要變更 BizTalk 應用程式，您就應該重複這個程序。</span><span class="sxs-lookup"><span data-stu-id="242e6-112">You should repeat this process whenever you change the BizTalk applications.</span></span> <span data-ttu-id="242e6-113">如需詳細資訊，請參閱[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="242e6-113">For more information, see [How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="242e6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="242e6-114">See Also</span></span>  
 [<span data-ttu-id="242e6-115">備份執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="242e6-115">Backing Up a Computer Running BizTalk Server</span></span>](../core/backing-up-a-computer-running-biztalk-server.md)