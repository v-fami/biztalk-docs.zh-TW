---
title: "VisualStudioHostRestart （應用程式部署範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0b82627-1552-479d-a083-cdc9fe4843c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74289ae59ef96c579b3c132fd76f1d0e8e77cf13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="visualstudiohostrestart-application-deployment-sample"></a><span data-ttu-id="8f7bc-102">VisualStudioHostRestart (應用程式部署範例)</span><span class="sxs-lookup"><span data-stu-id="8f7bc-102">VisualStudioHostRestart (Application Deployment Sample)</span></span>
<span data-ttu-id="8f7bc-103">本主題會說明如何使用 VisualStudioHostRestart 範例指令碼，重新啟動本機電腦上 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 所執行的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-103">This topic explains how to use the VisualStudioHostRestart sample script to restart a host instance running under [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="8f7bc-104">您可以在重新部署 Visual Studio 中的組件時使用這個指令碼，以便 BizTalk Server 執行階段立即接受變更。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-104">You can use this script when redeploying assemblies in Visual Studio so that the BizTalk Server runtime immediately picks up the changes.</span></span> <span data-ttu-id="8f7bc-105">此外，您可以用這個選項來重新啟動主控件執行個體，這個選項可在專案的 [部署] 屬性中加以設定。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-105">Alternatively, you can use the option to restart host instances, which you can set in Deployment properties for the project.</span></span> <span data-ttu-id="8f7bc-106">如需詳細資訊，請參閱[如何在 Visual Studio 中設定部署屬性](../core/how-to-set-deployment-properties-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-106">For more information, see [How to Set Deployment Properties in Visual Studio](../core/how-to-set-deployment-properties-in-visual-studio.md).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="8f7bc-107">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="8f7bc-107">What This Sample Does</span></span>  
 <span data-ttu-id="8f7bc-108">這個範例指令碼會依序執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="8f7bc-108">This sample script performs the following actions, in order:</span></span>  
  
1.  <span data-ttu-id="8f7bc-109">停止本機電腦上的所有內含式主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-109">Stops all in-process host instances on the local computer.</span></span>  
  
2.  <span data-ttu-id="8f7bc-110">啟動本機電腦上的所有內含式主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-110">Starts all in-process host instances on the local computer.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="8f7bc-111">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="8f7bc-111">Where to Find This Sample</span></span>  
 <span data-ttu-id="8f7bc-112">此範例位於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，如下所示的安裝資料夾： *\<範例路徑 >*\Application Deployment\VisualStudioHostRestart。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-112">The sample is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation folder, as follows: *\<Samples path>*\Application Deployment\VisualStudioHostRestart.</span></span>  
  
 <span data-ttu-id="8f7bc-113">此範例包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="8f7bc-113">The sample includes the following file:</span></span>  
  
-   <span data-ttu-id="8f7bc-114">RestartBizTalkHostInstances.vbs</span><span class="sxs-lookup"><span data-stu-id="8f7bc-114">RestartBizTalkHostInstances.vbs</span></span>  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="8f7bc-115">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="8f7bc-115">How to Use This Sample</span></span>  
 <span data-ttu-id="8f7bc-116">請使用下列程序來執行此範例。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-116">Use the following procedures to run this sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="8f7bc-117">執行範例</span><span class="sxs-lookup"><span data-stu-id="8f7bc-117">To run the sample</span></span>  
  
-   <span data-ttu-id="8f7bc-118">執行 RestartBizTalkHostInstances.vbs。</span><span class="sxs-lookup"><span data-stu-id="8f7bc-118">Run RestartBizTalkHostInstances.vbs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f7bc-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f7bc-119">See Also</span></span>  
 <span data-ttu-id="8f7bc-120">[應用程式部署 （BizTalk Server 範例資料夾）](../core/application-deployment-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="8f7bc-120">[Application Deployment (BizTalk Server Samples Folder)](../core/application-deployment-biztalk-server-samples-folder.md) </span></span>  
 <span data-ttu-id="8f7bc-121">[部署 BizTalk 組件從 Visual Studio 到 BizTalk 應用程式](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="8f7bc-121">[Deploying BizTalk Assemblies from Visual Studio into a BizTalk Application](../core/deploying-biztalk-assemblies-from-visual-studio-into-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="8f7bc-122">部署 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="8f7bc-122">Deploying BizTalk Applications</span></span>](../core/deploying-biztalk-applications.md)