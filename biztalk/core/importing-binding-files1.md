---
title: "匯入繫結 Files1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- CLASSPATH environment variable
- importing binding files
- cleaning target computer
ms.assetid: b2a9b19b-2d3d-45ea-bd92-a2501791b86a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12fca64580b692f01834b48085aa2d88085fb743
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="28511-102">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="28511-102">Importing Binding Files</span></span>
<span data-ttu-id="28511-103">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="28511-103">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="28511-104">CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="28511-104">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="28511-105">確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="28511-105">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="28511-106">在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="28511-106">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="28511-107">PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="28511-107">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="28511-108">如需詳細資訊，請參閱[部署限制](../core/deployment-limitations3.md)。</span><span class="sxs-lookup"><span data-stu-id="28511-108">For more information, see [Deployment Limitations](../core/deployment-limitations3.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28511-109">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="28511-109">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="28511-110">當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="28511-110">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="28511-111">如需有關匯入繫結檔案的逐步指示，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜如何將繫結匯入 BizTalk 群組＞主題。</span><span class="sxs-lookup"><span data-stu-id="28511-111">For step-by-step directions about importing binding files, see the topic "How to Import Bindings into a BizTalk Group" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="cleaning-the-target-computer"></a><span data-ttu-id="28511-112">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="28511-112">Cleaning the Target Computer</span></span>  
 <span data-ttu-id="28511-113">請遵循下列步驟清除目標電腦，以部署新應用程式。</span><span class="sxs-lookup"><span data-stu-id="28511-113">Follow these steps to clean the target computer for deploying the new application.</span></span>  
  
#### <a name="to-clean-the-target-computer"></a><span data-ttu-id="28511-114">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="28511-114">To clean the target computer</span></span>  
  
-   <span data-ttu-id="28511-115">移除協調流程所繫結的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="28511-115">Remove send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="28511-116">如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="28511-116">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
     <span data-ttu-id="28511-117">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="28511-117">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
     <span data-ttu-id="28511-118">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**</span><span class="sxs-lookup"><span data-stu-id="28511-118">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
     <span data-ttu-id="28511-119">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="28511-119">For example, at a command prompt, run:</span></span>  
  
     <span data-ttu-id="28511-120">**cscript RemoveSendPort.vbs\<傳送埠名稱 >**</span><span class="sxs-lookup"><span data-stu-id="28511-120">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28511-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28511-121">See Also</span></span>  
 [<span data-ttu-id="28511-122">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="28511-122">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies5.md)