---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-peoplesoft-enterprise/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 907c21377a6affd5a99576137a5babaa1626c135
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="import-binding-files"></a><span data-ttu-id="f1db4-101">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="f1db4-101">Import Binding Files</span></span>

## <a name="overview"></a><span data-ttu-id="f1db4-102">概觀</span><span class="sxs-lookup"><span data-stu-id="f1db4-102">Overview</span></span>
<span data-ttu-id="f1db4-103">使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="f1db4-103">Before you use [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="f1db4-104">CLASSPATH 指向 PeopleSoft 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="f1db4-104">The CLASSPATH is pointing to a specific location for the PeopleSoft-specific files.</span></span> <span data-ttu-id="f1db4-105">確認這些檔案的位置在新電腦上相同，或編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f1db4-105">Verify that the location of these files is the same on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="f1db4-106">在新電腦上回應的資料夾必須存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f1db4-106">The folders for the responses must exist and be identical on the new computer—or edit the binding file.</span></span>  
  
-   <span data-ttu-id="f1db4-107">PeopleSoft Enterprise 系統密碼 (如果出現在組態中) 以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="f1db4-107">PeopleSoft Enterprise system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="f1db4-108">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="f1db4-108">Deployment overwrites receive location configuration.</span></span> <span data-ttu-id="f1db4-109">當您在目標電腦上部署繫結檔案和組件，在匯入 XML 繫結檔案時，傳送埠和接收位置會遭取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="f1db4-109">When you deploy a binding file and assembly on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
 <span data-ttu-id="f1db4-110">如需有關匯入繫結檔案的逐步指示，請參閱 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 文件中的＜如何將繫結匯入 BizTalk 群組＞主題。</span><span class="sxs-lookup"><span data-stu-id="f1db4-110">For step-by-step directions about importing binding files, see the topic "How to Import Bindings into a BizTalk Group" in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] documentation.</span></span>  
  
## <a name="clean-the-target-computer"></a><span data-ttu-id="f1db4-111">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="f1db4-111">Clean the Target Computer</span></span>  
<span data-ttu-id="f1db4-112">若要清除目標電腦，部署新的應用程式、 移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="f1db4-112">To clean the target computer for deploying the new application, remove send ports and receive locations bound to the orchestration.</span></span>  
  
<span data-ttu-id="f1db4-113">如果目標電腦上尚未安裝 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="f1db4-113">If you do not have Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] installed on the target computer, you may remove the ports by running these scripts:</span></span>  
  
<span data-ttu-id="f1db4-114">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs**</span><span class="sxs-lookup"><span data-stu-id="f1db4-114">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs**</span></span>  
  
<span data-ttu-id="f1db4-115">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs**</span><span class="sxs-lookup"><span data-stu-id="f1db4-115">**\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs**</span></span>  
  
<span data-ttu-id="f1db4-116">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="f1db4-116">For example, at a command prompt, run:</span></span>  
  
<span data-ttu-id="f1db4-117">**cscript RemoveSendPort.vbs\<傳送埠名稱\>**</span><span class="sxs-lookup"><span data-stu-id="f1db4-117">**cscript RemoveSendPort.vbs \<Send port name\>**</span></span>  
  
