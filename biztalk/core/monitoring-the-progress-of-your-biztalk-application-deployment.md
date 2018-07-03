---
title: 監控 BizTalk 應用程式部署的進度 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- monitoring, deploying
- applications, monitoring
- deploying [applications], monitoring
- monitoring, applications
ms.assetid: a69a8288-0203-440f-9805-52786525e193
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07beea810ff64c807685b8170009d5204ede1af7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37001151"
---
# <a name="monitoring-the-progress-of-your-biztalk-application-deployment"></a><span data-ttu-id="5123e-102">監控 BizTalk 應用程式部署的進度</span><span class="sxs-lookup"><span data-stu-id="5123e-102">Monitoring the Progress of Your BizTalk Application Deployment</span></span>
<span data-ttu-id="5123e-103">有兩個方法可以監控 BizTalk 應用程式部署的進度：</span><span class="sxs-lookup"><span data-stu-id="5123e-103">You can monitor the progress of your BizTalk application deployment in two ways:</span></span>  
  
- <span data-ttu-id="5123e-104">**BizTalk 安裝記錄檔**： 您可以查閱 BizTalk Server 產生安裝記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5123e-104">**BizTalk installation log**: You can consult the installation log that BizTalk Server generates.</span></span> <span data-ttu-id="5123e-105">安裝記錄檔位於 %SystemDrive%\Documents and Settings\\<*目前的使用者*\>\application data\microsoft\biztalk Server\Deployment。</span><span class="sxs-lookup"><span data-stu-id="5123e-105">Installation logs are located in %SystemDrive%\Documents and Settings\\<*current user*\>\Application Data\Microsoft\BizTalk Server\Deployment.</span></span>  
  
- <span data-ttu-id="5123e-106">**本機事件記錄檔**： 您可以追蹤本機事件記錄檔中安裝的進度。</span><span class="sxs-lookup"><span data-stu-id="5123e-106">**Local event log**: You can track the progress of an installation in the local event log.</span></span> <span data-ttu-id="5123e-107">因此，您可以以個別伺服器為基礎來追蹤自訂安裝動作。</span><span class="sxs-lookup"><span data-stu-id="5123e-107">Therefore, you can track custom installation actions on a per-server basis.</span></span>  
  
- <span data-ttu-id="5123e-108">**Windows Installer 記錄**: Microsoft Windows 安裝程式會建立自訂動作的動作記錄在本機電腦上的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5123e-108">**Windows Installer log**: Microsoft Windows Installer creates a log file on the local computer that logs the actions of a custom action.</span></span> <span data-ttu-id="5123e-109">您可以使用 msiexec 命令的 /log 選項來指定這個記錄檔。</span><span class="sxs-lookup"><span data-stu-id="5123e-109">You can specify this log file by using the /log option of the msiexec command.</span></span> <span data-ttu-id="5123e-110">如需詳細資訊，請參閱 Windows Installer 的文件。</span><span class="sxs-lookup"><span data-stu-id="5123e-110">For more information, see the documentation for Windows Installer.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5123e-111">部署或解除部署屬性結構描述可能會公開機密資料，而之後可能會在追蹤期間公開機密資訊。</span><span class="sxs-lookup"><span data-stu-id="5123e-111">Deploying or undeploying a property schema may expose sensitive data, and subsequently expose sensitive information during tracking.</span></span> <span data-ttu-id="5123e-112">每當部署或解除部署包含屬性結構描述的組件時，事件檢視器會將事件記錄在 Windows 應用程式事件記錄中。</span><span class="sxs-lookup"><span data-stu-id="5123e-112">Whenever an assembly containing a property schema is deployed or undeployed, the event viewer logs an event in the Windows Application Event Log.</span></span> <span data-ttu-id="5123e-113">您應檢查事件日誌檔中的這些訊息，確保所有組件部署活動都符合任何機密資料的原則</span><span class="sxs-lookup"><span data-stu-id="5123e-113">You should check the event log for these messages to ensure that all assembly deployment activities are in line with your policies for any sensitive data.</span></span> <span data-ttu-id="5123e-114">(部署為事件記錄檔產生的訊息: 「 使用者 」{1}「 已部署組件 」{0}"包含屬性結構描述 」。</span><span class="sxs-lookup"><span data-stu-id="5123e-114">(The message generated to the Event Log for deployment is: "The user "{1}" deployed the assembly "{0}" containing property schemas."</span></span> <span data-ttu-id="5123e-115">解除部署是產生事件記錄檔的訊息: 「 使用者 」{1}"已解除部署組件 」{0}"包含屬性結構描述 」。)</span><span class="sxs-lookup"><span data-stu-id="5123e-115">The message generated to the Event Log for undeployment is: "The user "{1}" undeployed the assembly "{0}" containing property schemas.")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5123e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5123e-116">See Also</span></span>  
 [<span data-ttu-id="5123e-117">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="5123e-117">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)