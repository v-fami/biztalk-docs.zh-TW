---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-rendezvous/
redirect_document_id: true
ROBOTS: NOINDEX
ms.openlocfilehash: 12e8a37da357693b97659c1717ead750e558e62b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018441"
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="e2a12-101">如何清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="e2a12-101">How to Clean the Target Computer</span></span>
<span data-ttu-id="e2a12-102">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="e2a12-102">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="e2a12-103">當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。</span><span class="sxs-lookup"><span data-stu-id="e2a12-103">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="e2a12-104">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="e2a12-104">To clean the target computer</span></span>  
  
- <span data-ttu-id="e2a12-105">移除協調流程所繫結的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="e2a12-105">Remove send ports and receive locations bound to the orchestration.</span></span>  
  
   <span data-ttu-id="e2a12-106">如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="e2a12-106">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
  - [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="e2a12-107">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="e2a12-107">SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
  - [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="e2a12-108">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="e2a12-108">SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="e2a12-109">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="e2a12-109">For example, at a command prompt, run:</span></span>  
  
     <span data-ttu-id="e2a12-110">**cscript RemoveSendPort.vbs\<傳送埠名稱\>**</span><span class="sxs-lookup"><span data-stu-id="e2a12-110">**cscript RemoveSendPort.vbs \<Send port name\>**</span></span>  
  
