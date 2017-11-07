---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 8a2b78ee2e8ec75c6ce83a8b78d1e779f012f324
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="import-binding-files"></a><span data-ttu-id="301ec-101">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="301ec-101">Import Binding Files</span></span>

## <a name="overview"></a><span data-ttu-id="301ec-102">概觀</span><span class="sxs-lookup"><span data-stu-id="301ec-102">Overview</span></span>
<span data-ttu-id="301ec-103">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="301ec-103">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="301ec-104">CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="301ec-104">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="301ec-105">確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="301ec-105">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="301ec-106">在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="301ec-106">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="301ec-107">PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="301ec-107">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="301ec-108">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="301ec-108">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="301ec-109">當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="301ec-109">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="301ec-110">如需有關匯入繫結檔案的逐步指示，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜如何將繫結匯入 BizTalk 群組＞主題。</span><span class="sxs-lookup"><span data-stu-id="301ec-110">For step-by-step directions about importing binding files, see the topic "How to Import Bindings into a BizTalk Group" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="301ec-111">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="301ec-111">Clean the Target Computer</span></span>  
<span data-ttu-id="301ec-112">若要清除目標電腦，部署新的應用程式、 移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="301ec-112">To clean the target computer for deploying the new application, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="301ec-113">如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="301ec-113">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
<span data-ttu-id="301ec-114">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="301ec-114">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
<span data-ttu-id="301ec-115">**\<Microsoft BizTalk Server > \SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**</span><span class="sxs-lookup"><span data-stu-id="301ec-115">**\<Microsoft BizTalk Server>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
<span data-ttu-id="301ec-116">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="301ec-116">For example, at a command prompt, run:</span></span>  
  
<span data-ttu-id="301ec-117">**cscript RemoveSendPort.vbs\<傳送埠名稱 >**</span><span class="sxs-lookup"><span data-stu-id="301ec-117">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
