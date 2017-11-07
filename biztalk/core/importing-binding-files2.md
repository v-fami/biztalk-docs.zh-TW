---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 0bc5b29ff129b145d6b55cbe44ea3aa6a97def76
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="0c069-101">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="0c069-101">Importing Binding Files</span></span>
<span data-ttu-id="0c069-102">本節提供有關部署 BizTalk Adapter for JD Edwards EnterpriseOne 時之匯入程序的資訊。</span><span class="sxs-lookup"><span data-stu-id="0c069-102">This topic provides some information concerning the import process when you deploy BizTalk Adapter for JD Edwards EnterpriseOne.</span></span> <span data-ttu-id="0c069-103">當您在目標電腦上重新部署繫結檔案 (和組件)，傳送埠和接收位置會在重新匯入 XML 繫結檔案時，被取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="0c069-103">When you redeploy a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are reimported.</span></span>  
  
### <a name="to-clean-the-target-computer"></a><span data-ttu-id="0c069-104">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="0c069-104">To clean the target computer</span></span>  
  
-   <span data-ttu-id="0c069-105">移除協調流程所繫結的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="0c069-105">Remove Send ports and Receive locations bound to the orchestration.</span></span>  
  
     <span data-ttu-id="0c069-106">如果目標電腦上未安裝 Visual Studio，您可以執行下列指令碼來移除連接埠：</span><span class="sxs-lookup"><span data-stu-id="0c069-106">If you do not have Visual Studio installed on the target computer, you can remove the ports by running the scripts:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="0c069-107">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="0c069-107">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="0c069-108">Remove Send Port\VBScript\RemoveSendPort.vbs</span><span class="sxs-lookup"><span data-stu-id="0c069-108">Remove Send Port\VBScript\RemoveSendPort.vbs</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="0c069-109">SDK\Samples\Admin\WMI\\</span><span class="sxs-lookup"><span data-stu-id="0c069-109">SDK\Samples\Admin\WMI\\</span></span>  
  
     <span data-ttu-id="0c069-110">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span><span class="sxs-lookup"><span data-stu-id="0c069-110">Remove Receive Port\VBScript\RemoveReceivePort.vbs</span></span>  
  
     <span data-ttu-id="0c069-111">例如，在命令提示字元下執行：</span><span class="sxs-lookup"><span data-stu-id="0c069-111">For example, from a command prompt run:</span></span>  
  
     <span data-ttu-id="0c069-112">**cscript RemoveSendPort.vbs\<傳送埠名稱 >**</span><span class="sxs-lookup"><span data-stu-id="0c069-112">**cscript RemoveSendPort.vbs \<Send port name>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c069-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c069-113">See Also</span></span>  
 [<span data-ttu-id="0c069-114">匯入 JD Edwards EnterpriseOne 應用程式</span><span class="sxs-lookup"><span data-stu-id="0c069-114">Import the JD Edwards EnterpriseOne app</span></span>](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md)