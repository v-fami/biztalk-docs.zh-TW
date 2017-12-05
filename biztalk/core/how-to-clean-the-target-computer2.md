---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-tibco-enterprise-message-service/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 794ab5e4ed28464ed704d27da05390dad6199224
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-clean-the-target-computer"></a><span data-ttu-id="c2e34-101">如何清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="c2e34-101">How to Clean the Target Computer</span></span>
<span data-ttu-id="c2e34-102">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="c2e34-102">Deployment overwrites the receive location configuration.</span></span> <span data-ttu-id="c2e34-103">當您在目標電腦上部署繫結檔案 (和組件)，在匯入 XML 繫結檔案時，傳送埠和接收位置會被 XML 繫結檔案中的傳送埠和接收位置所取代。</span><span class="sxs-lookup"><span data-stu-id="c2e34-103">When you deploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="c2e34-104">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="c2e34-104">To clean the target computer</span></span>  
  
-   <span data-ttu-id="c2e34-105">移除協調流程所繫結的所有傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="c2e34-105">Remove any send ports and receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="c2e34-106">如果目標電腦上尚未安裝 Microsoft Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="c2e34-106">If you do not have Microsoft Visual Studio installed on the target computer, you can remove the ports by running these scripts:</span></span>  
  
     <span data-ttu-id="c2e34-107">\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove 傳送 Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="c2e34-107">\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     <span data-ttu-id="c2e34-108">\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove 接收 Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="c2e34-108">\<Microsoft BizTalk Server\>\SDK\Samples\Admin\WMI\Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="c2e34-109">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="c2e34-109">For example, at a command prompt, run:</span></span>  
  
     <span data-ttu-id="c2e34-110">**cscript RemoveSendPort.vbs\<傳送埠名稱\>**</span><span class="sxs-lookup"><span data-stu-id="c2e34-110">**cscript RemoveSendPort.vbs \<Send port name\>**</span></span>  
  
