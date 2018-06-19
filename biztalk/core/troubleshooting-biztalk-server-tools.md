---
title: 疑難排解 BizTalk Server 工具 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 038a5f5c-d6eb-42db-88d6-70f3deba7a8a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b7aedd8977042d15176781b0595bd5bb225a2fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279766"
---
# <a name="troubleshooting-biztalk-server-tools"></a><span data-ttu-id="006f6-102">BizTalk Server 工具疑難排解</span><span class="sxs-lookup"><span data-stu-id="006f6-102">Troubleshooting BizTalk Server Tools</span></span>
<span data-ttu-id="006f6-103">本主題提供集中的位置來存放使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的工具時經常會遇到之問題的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="006f6-103">This topic provides a centralized location for information about common problems encountered while using the tools included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="006f6-104">已知問題</span><span class="sxs-lookup"><span data-stu-id="006f6-104">Known Issues</span></span>  
  
### <a name="biztalk-server-tools-and-utilities-may-not-function-correctly-on-a-windows-system-that-supports-uac"></a><span data-ttu-id="006f6-105">BizTalk Server 工具和公用程式在支援 UAC 的 Windows 系統上可能無法正常運作</span><span class="sxs-lookup"><span data-stu-id="006f6-105">BizTalk Server Tools and Utilities May Not Function Correctly on a Windows System That Supports UAC</span></span>  
 <span data-ttu-id="006f6-106">**問題**</span><span class="sxs-lookup"><span data-stu-id="006f6-106">**Problem**</span></span>  
  
 <span data-ttu-id="006f6-107">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝在支援使用者帳戶控制 (UAC) 的系統上時，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的工具可能無法順利啟動，或無法正常運作。</span><span class="sxs-lookup"><span data-stu-id="006f6-107">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a system that supports User Account Control (UAC), the tools included with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may not launch successfully, or may not function correctly.</span></span>  
  
 <span data-ttu-id="006f6-108">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="006f6-108">**Cause**</span></span>  
  
 <span data-ttu-id="006f6-109">在執行已標示為特定權限等級的應用程式時，如果所需等級高於執行該應用程式的使用者的權限，UAC 會顯示提示，讓您將應用程式權限暫時提升至所需的等級。</span><span class="sxs-lookup"><span data-stu-id="006f6-109">When running an application that has been flagged for a specific privilege level, if the required level is higher than that of the user running the application, the UAC will display a prompt that allows you to temporarily elevate the application privilege to the required level.</span></span> <span data-ttu-id="006f6-110">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 隨附的工具並未啟用正確的旗標來自動要求權限提升，因此，工具會嘗試以執行應用程式的使用者目前的權限等級來執行，但如果需要更高權限，則執行會失敗。</span><span class="sxs-lookup"><span data-stu-id="006f6-110">The tools shipped with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have the correct flags enabled to automatically request privilege elevation, so the tool will attempt to run at the current privilege level of the user running the application and will fail if a higher privilege level is required.</span></span>  
  
 <span data-ttu-id="006f6-111">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="006f6-111">**Resolution**</span></span>  
  
 <span data-ttu-id="006f6-112">為了解決此問題，請以系統管理權限執行所有 BizTalk Server 工具。</span><span class="sxs-lookup"><span data-stu-id="006f6-112">To resolve this problem, run all BizTalk Server tools with Administrative privileges.</span></span> <span data-ttu-id="006f6-113">若要以系統管理權限執行一項工具，以滑鼠右鍵按一下應用程式，然後選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="006f6-113">To run a tool with Administrative privileges, right-click the application and then select **Run as administrator**.</span></span>  
  
 <span data-ttu-id="006f6-114">如需使用者帳戶控制的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=99167](http://go.microsoft.com/fwlink/?LinkId=99167)。</span><span class="sxs-lookup"><span data-stu-id="006f6-114">For more information about the User Account Control, see [http://go.microsoft.com/fwlink/?LinkId=99167](http://go.microsoft.com/fwlink/?LinkId=99167).</span></span>  
  
### <a name="sometimes-biztalk-mapper-toolbox-may-appear-empty"></a><span data-ttu-id="006f6-115">BizTalk 對應工具工具箱有時可能會出現空白</span><span class="sxs-lookup"><span data-stu-id="006f6-115">Sometimes BizTalk Mapper Toolbox May Appear Empty</span></span>  
 <span data-ttu-id="006f6-116">**問題**</span><span class="sxs-lookup"><span data-stu-id="006f6-116">**Problem**</span></span>  
  
 <span data-ttu-id="006f6-117">有時候，當您在 Visual Studio 中開啟對應工具工具箱，看不到任何運算質工具箱中。</span><span class="sxs-lookup"><span data-stu-id="006f6-117">Sometimes, when you open the Mapper toolbox in Visual Studio, you do not see any functoids in the toolbox.</span></span>  
  
 <span data-ttu-id="006f6-118">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="006f6-118">**Cause**</span></span>  
  
 <span data-ttu-id="006f6-119">可能是由安裝/解除安裝 Visual Studio 增益集和 （或） patch(es) 可能損毀。</span><span class="sxs-lookup"><span data-stu-id="006f6-119">Might be a probable corruption by install/uninstall of Visual Studio add-ins and/or patch(es).</span></span>  
  
 <span data-ttu-id="006f6-120">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="006f6-120">**Resolution**</span></span>  
  
 <span data-ttu-id="006f6-121">若要解決這個問題：</span><span class="sxs-lookup"><span data-stu-id="006f6-121">To resolve this problem:</span></span>  
  
1.  <span data-ttu-id="006f6-122">關閉 Visual Studio 的所有執行的執行個體。</span><span class="sxs-lookup"><span data-stu-id="006f6-122">Close all running instances of Visual Studio.</span></span>  
  
2.  <span data-ttu-id="006f6-123">啟動**Visual Studio 命令提示字元**身為系統管理員。</span><span class="sxs-lookup"><span data-stu-id="006f6-123">Start **Visual Studio Command Prompt** as an administrator.</span></span>  
  
3.  <span data-ttu-id="006f6-124">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="006f6-124">At the command prompt, type the following command:</span></span>  
  
    ```  
    devenv.exe /setup  
    ```