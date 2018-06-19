---
title: 管理前置或後置處理指令碼 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 107ada12-fef2-4b56-8ff8-228c13761104
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18926a0c51e5ab5f65b32373d20b2931ccaa627d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262470"
---
# <a name="manage-pre--and-post-processing-scripts"></a><span data-ttu-id="c52ab-102">管理前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="c52ab-102">Manage Pre- and Post-processing Scripts</span></span>

## <a name="overview"></a><span data-ttu-id="c52ab-103">概觀</span><span class="sxs-lookup"><span data-stu-id="c52ab-103">Overview</span></span>
<span data-ttu-id="c52ab-104">本節提供使用 BizTalk Server 管理主控台或 BTSTask 命令列工具以管理前置或後置處理指令碼的指示。</span><span class="sxs-lookup"><span data-stu-id="c52ab-104">This section provides instructions on using the BizTalk Server Administration console or the BTSTask command-line tool to manage pre- and post-processing scripts.</span></span> <span data-ttu-id="c52ab-105">您可以建立想要在匯入、安裝或解除安裝 (移除) BizTalk 應用程式時執行的指令碼，然後將該指令碼加入至應用程式。</span><span class="sxs-lookup"><span data-stu-id="c52ab-105">You can create a script that you want to have run when a BizTalk application is imported, installed, or uninstalled (removed), and then add the script to the application.</span></span> <span data-ttu-id="c52ab-106">當您加入指令碼時，請指定它是前置處理指令碼 (會在匯入或安裝前，以及在解除安裝後執行)，還是後置處理指令碼 (會在匯入或安裝後，以及在解除安裝前執行)。</span><span class="sxs-lookup"><span data-stu-id="c52ab-106">When you add a script, you specify whether it is a pre-preprocessing script, which runs before import, installation and after uninstallation, or a post-processing script, which runs after import or installation, and before uninstallation.</span></span>  
  
 <span data-ttu-id="c52ab-107">如果您在匯出應用程式時選取指令碼，則該指令碼會包含在應用程式的 .msi 檔案中。</span><span class="sxs-lookup"><span data-stu-id="c52ab-107">If you select the script when exporting the application, the script is included in the .msi file for the application.</span></span> <span data-ttu-id="c52ab-108">當您安裝、解除安裝或匯入應用程式時，指令碼就會依照您撰寫指令碼的方式自動執行。</span><span class="sxs-lookup"><span data-stu-id="c52ab-108">When you install, uninstall, or import the application, the script automatically runs, depending on how you have written the script.</span></span> <span data-ttu-id="c52ab-109">如需有關建立和使用指令碼的詳細資訊，請參閱[使用前置和後置處理指令碼，以自訂應用程式部署](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="c52ab-109">For more information about creating and using scripts, see [Using Pre- and Post-processing Scripts to Customize Application Deployment](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c52ab-110">您可以使用 Microsoft Windows Management Instrumentation (WMI) 物件模型，建立和執行會自動化系統管理工作的指令碼。</span><span class="sxs-lookup"><span data-stu-id="c52ab-110">You can use Microsoft Windows Management Instrumentation (WMI) Object Model to create and run scripts that automate administrative tasks.</span></span> <span data-ttu-id="c52ab-111">如需使用 WMI 的詳細資訊，請參閱**WMI 類別參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="c52ab-111">For information about using WMI, see the **WMI Class Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="c52ab-112">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="c52ab-112">Next steps</span></span> 
  
-   [<span data-ttu-id="c52ab-113">應用程式中加入前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="c52ab-113">Add a Pre- or Post-processing Script to an Application</span></span>](../core/how-to-add-a-pre-or-post-processing-script-to-an-application.md)  
  
-   [<span data-ttu-id="c52ab-114">變更前置或後置處理指令碼的目的地位置</span><span class="sxs-lookup"><span data-stu-id="c52ab-114">Change the Destination Location of a Pre- or Post-processing Script</span></span>](../core/how-to-change-the-destination-location-of-a-pre-or-post-processing-script.md)  
  
-   [<span data-ttu-id="c52ab-115">從應用程式移除前置或後置處理指令碼</span><span class="sxs-lookup"><span data-stu-id="c52ab-115">Remove a Pre- or Post-processing Script from an Application</span></span>](../core/how-to-remove-a-pre-or-post-processing-script-from-an-application.md)