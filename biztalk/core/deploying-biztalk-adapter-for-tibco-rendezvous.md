---
title: 匯入繫結的 TIBCO Rendezvous |Microsoft Docs
description: 部署您的 BizTalk Adapter for TIBCO Rendezvous 使用 BizTalk Server 中匯入繫結功能的應用程式
ms.custom: ''
ms.date: 10/24/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec5751a9-0a08-4cf8-a3ef-e51e488a4180
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb362afb23b165c31df34adf521be81f93a621f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994007"
---
# <a name="deploy-tibco-rendezvous-ports-and-assemblies"></a><span data-ttu-id="2492e-103">部署 TIBCO Rendezvous 連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="2492e-103">Deploy TIBCO Rendezvous ports and assemblies</span></span>
  
## <a name="overview"></a><span data-ttu-id="2492e-104">概觀</span><span class="sxs-lookup"><span data-stu-id="2492e-104">Overview</span></span>
<span data-ttu-id="2492e-105">您可以使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在目標電腦上複製連接埠和組件。</span><span class="sxs-lookup"><span data-stu-id="2492e-105">Using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can duplicate ports and assemblies on a target computer.</span></span> <span data-ttu-id="2492e-106">精靈會將傳送埠/接收位置組態匯出到 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="2492e-106">The wizard exports the send ports/receive location configuration into an XML file.</span></span>  
  
 <span data-ttu-id="2492e-107">您可以使用 BizTalk Server 執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2492e-107">You use BizTalk Server to do the following tasks:</span></span>  
  
- <span data-ttu-id="2492e-108">在BizTalk 組態資料庫中部署或移除 BizTalk Server 組件。</span><span class="sxs-lookup"><span data-stu-id="2492e-108">Deploy or remove BizTalk Server assemblies in a BizTalk Configuration database.</span></span>  
  
- <span data-ttu-id="2492e-109">在全域組件快取 (GAC) 中安裝或解除安裝組件。</span><span class="sxs-lookup"><span data-stu-id="2492e-109">Install or uninstall the assemblies in the global assembly cache (GAC).</span></span>  
  
- <span data-ttu-id="2492e-110">將 BizTalk Server 組件繫結資訊匯入到繫結檔案，或是將它從繫結檔案中匯出。</span><span class="sxs-lookup"><span data-stu-id="2492e-110">Import or export BizTalk Server assembly binding information to and from binding files.</span></span>  
  
  <span data-ttu-id="2492e-111">如需有關如何使用資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]若要將連接埠和組件的部署，請參閱[如何匯出 BizTalk 應用程式的繫結](../core/how-to-export-bindings-for-a-biztalk-application.md)。</span><span class="sxs-lookup"><span data-stu-id="2492e-111">For information about how to use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to deploy ports and assemblies, see [How to Export Bindings for a BizTalk Application](../core/how-to-export-bindings-for-a-biztalk-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2492e-112">Microsoft BizTalk Adapter for TIBCO Rendezvous 只要求來源 (開發) 電腦上必須有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2492e-112">Microsoft BizTalk Adapter for TIBCO Rendezvous only requires that you have Visual Studio on a source (development) computer.</span></span> <span data-ttu-id="2492e-113">實際執行電腦上不需要有 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2492e-113">Visual Studio is not required on the production computer.</span></span>  

## <a name="confirm-your-setup"></a><span data-ttu-id="2492e-114">確認您的設定</span><span class="sxs-lookup"><span data-stu-id="2492e-114">Confirm your setup</span></span>

<span data-ttu-id="2492e-115">在您使用之前[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]匯入繫結檔案，確認有用於回應的資料夾存在，及它們完全相同的新的電腦上，或者您也必須編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="2492e-115">Before you use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, confirm that the folders for the responses exist, and that they are identical on the new computer, or you must edit the binding file.</span></span>  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="2492e-116">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="2492e-116">Clean the target computer</span></span>
<span data-ttu-id="2492e-117">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="2492e-117">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="2492e-118">當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。</span><span class="sxs-lookup"><span data-stu-id="2492e-118">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
<span data-ttu-id="2492e-119">在匯入之前，移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="2492e-119">Before you import, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="2492e-120">如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="2492e-120">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="2492e-121">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="2492e-121">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
- [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="2492e-122">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="2492e-122">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
<span data-ttu-id="2492e-123">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="2492e-123">For example, at a command prompt, run:</span></span>  
  
```
cscript RemoveSendPort.vbs \<Send port name\>
```
  
## <a name="next-steps"></a><span data-ttu-id="2492e-124">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="2492e-124">Next steps</span></span>
[<span data-ttu-id="2492e-125">使用 協調流程中的 BizTalk Server 例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="2492e-125">Use BizTalk Server Exception Handling in your orchestration</span></span>](../core/using-biztalk-server-exception-handling4.md)  
[<span data-ttu-id="2492e-126">疑難排解</span><span class="sxs-lookup"><span data-stu-id="2492e-126">Troubleshoot</span></span>](../core/troubleshooting-tibco-rendezvous.md)