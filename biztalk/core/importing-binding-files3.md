---
redirect_url: /biztalk/core/deploying-biztalk-adapter-for-jd-edwards-oneworld/
redirect_document_id: True
ROBOTS: NOINDEX
ms.openlocfilehash: 5c5cce40f3fbeb580ec7ba854d02cb243e1742b4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="8c51a-101">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="8c51a-101">Importing Binding Files</span></span>

## <a name="overview"></a><span data-ttu-id="8c51a-102">概觀</span><span class="sxs-lookup"><span data-stu-id="8c51a-102">Overview</span></span>
<span data-ttu-id="8c51a-103">使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="8c51a-103">Before you use the BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="8c51a-104">CLASSPATH 指向 JD Edwards 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="8c51a-104">The CLASSPATH is pointing to a specific location for the JD Edwards-specific files.</span></span> <span data-ttu-id="8c51a-105">確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="8c51a-105">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="8c51a-106">在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="8c51a-106">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="8c51a-107">JD Edwards 系統密碼 (如果出現在組態中) 會以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="8c51a-107">JD Edwards system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> 
  
> [!NOTE]
>  <span data-ttu-id="8c51a-108">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="8c51a-108">Deployment overwrites Receive Location configuration.</span></span> <span data-ttu-id="8c51a-109">在目標電腦上部署繫結檔案 (和組件) 時，傳送埠和接收位置會在匯入時被取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="8c51a-109">When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
## <a name="import-the-binding-files"></a><span data-ttu-id="8c51a-110">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="8c51a-110">Import the Binding Files</span></span>  
  
1.  <span data-ttu-id="8c51a-111">上**啟動**功能表上，指向**Program Files**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**啟動 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="8c51a-111">On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="8c51a-112">依序展開 BizTalk Server 管理**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8c51a-112">Expand BizTalk Server Administration, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="8c51a-113">以滑鼠右鍵按一下所需的應用程式，指向**匯入**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="8c51a-113">Right-click the desired application, point to **Import**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="8c51a-114">在**匯入繫結**對話方塊中，瀏覽並選取繫結檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="8c51a-114">In the **Import Bindings** dialog box, browse and select the binding files, and then click **Open**.</span></span>  
  
## <a name="cleaning-the-target-computer"></a><span data-ttu-id="8c51a-115">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="8c51a-115">Cleaning the Target Computer</span></span>  
<span data-ttu-id="8c51a-116">移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="8c51a-116">Remove the send ports and the receive locations that are bound to the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c51a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c51a-117">See Also</span></span>  
 <span data-ttu-id="8c51a-118">[將成品新增至 BizTalk 管理](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span><span class="sxs-lookup"><span data-stu-id="8c51a-118">[Add the artifacts to BizTalk Administration](../core/adding-biztalk-adapter-for-jd-edwards-oneworld.md) </span></span>  
 [<span data-ttu-id="8c51a-119">匯入 JD Edwards OneWorld 應用程式</span><span class="sxs-lookup"><span data-stu-id="8c51a-119">Import the JD Edwards OneWorld app</span></span>](deploying-biztalk-adapter-for-jd-edwards-oneworld.md)