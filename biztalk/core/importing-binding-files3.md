---
title: "匯入繫結 Files3 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding files, importing
- target computer, cleaning
- importing binding files
- cleaning target computer
ms.assetid: 955bb3e1-3dbc-43ce-9126-205d838ae662
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1d95c40e3e556068e15a269ee4cbb7e995429a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-binding-files"></a><span data-ttu-id="f8ed3-102">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="f8ed3-102">Importing Binding Files</span></span>
<span data-ttu-id="f8ed3-103">使用 BizTalk Server 匯入繫結檔案之前，請確認下列項目：</span><span class="sxs-lookup"><span data-stu-id="f8ed3-103">Before you use the BizTalk Server to import a binding file, verify the following:</span></span>  
  
-   <span data-ttu-id="f8ed3-104">CLASSPATH 指向 JD Edwards 專屬檔案的特定位置。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-104">The CLASSPATH is pointing to a specific location for the JD Edwards-specific files.</span></span> <span data-ttu-id="f8ed3-105">確認這些檔案的位置在新電腦上是相同的，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-105">Verify that the location of these files is the same on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="f8ed3-106">在新電腦上用於存放回應的資料夾存在且相同，否則請編輯繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-106">The folders for the responses exist and are identical on the new computer, or edit the binding file.</span></span>  
  
-   <span data-ttu-id="f8ed3-107">JD Edwards 系統密碼 (如果出現在組態中) 會以 ***** 格式儲存在繫結檔案中。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-107">JD Edwards system passwords, if present in the configuration, are saved as ***** in the binding file.</span></span> <span data-ttu-id="f8ed3-108">如需詳細資訊，請參閱[部署限制](../core/deployment-limitations2.md)。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-108">For more information, see [Deployment Limitations](../core/deployment-limitations2.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8ed3-109">部署會覆寫接收位置組態。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-109">Deployment overwrites Receive Location configuration.</span></span> <span data-ttu-id="f8ed3-110">在目標電腦上部署繫結檔案 (和組件) 時，傳送埠和接收位置會在匯入時被取代為 XML 繫結檔案中的傳送埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-110">When deploying a binding file (and assembly) on a target computer, the send ports and receive locations are replaced with those in the XML binding file when they are imported.</span></span>  
  
## <a name="importing-the-binding-files"></a><span data-ttu-id="f8ed3-111">匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="f8ed3-111">Importing the Binding Files</span></span>  
 <span data-ttu-id="f8ed3-112">您可以使用下列程序，匯入繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-112">Use the following procedure to import the binding files.</span></span>  
  
#### <a name="to-import-the-binding-files"></a><span data-ttu-id="f8ed3-113">若要匯入繫結檔案</span><span class="sxs-lookup"><span data-stu-id="f8ed3-113">To import the binding files</span></span>  
  
1.  <span data-ttu-id="f8ed3-114">上**啟動**功能表上，指向**Program Files**，指向  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 管理**啟動 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-114">On the **Start** menu, point to **Program Files**, point to **Microsoft BizTalk Server**, and then click **BizTalk Server Administration** to start the BizTalk Server Administration Console.</span></span>  
  
2.  <span data-ttu-id="f8ed3-115">依序展開 BizTalk Server 管理**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-115">Expand BizTalk Server Administration, expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="f8ed3-116">以滑鼠右鍵按一下所需的應用程式，指向**匯入**，然後按一下 **繫結**。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-116">Right-click the desired application, point to **Import**, and then click **Bindings**.</span></span>  
  
4.  <span data-ttu-id="f8ed3-117">在**匯入繫結**對話方塊中，瀏覽並選取繫結檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-117">In the **Import Bindings** dialog box, browse and select the binding files, and then click **Open**.</span></span>  
  
## <a name="cleaning-the-target-computer"></a><span data-ttu-id="f8ed3-118">清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="f8ed3-118">Cleaning the Target Computer</span></span>  
 <span data-ttu-id="f8ed3-119">使用下列程序來清除目標電腦。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-119">Use the following procedure to clean the target computer.</span></span>  
  
#### <a name="to-clean-the-target-computer"></a><span data-ttu-id="f8ed3-120">若要清除目標電腦</span><span class="sxs-lookup"><span data-stu-id="f8ed3-120">To clean the target computer</span></span>  
  
-   <span data-ttu-id="f8ed3-121">移除傳送埠和接收位置繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="f8ed3-121">Remove the send ports and the receive locations that are bound to the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8ed3-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8ed3-122">See Also</span></span>  
 <span data-ttu-id="f8ed3-123">[建立 JD Edwards OneWorld 傳送處理常式](../core/creating-jd-edwards-oneworld-send-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="f8ed3-123">[Creating JD Edwards OneWorld Send Handlers](../core/creating-jd-edwards-oneworld-send-handlers.md) </span></span>  
 [<span data-ttu-id="f8ed3-124">部署連接埠和組件</span><span class="sxs-lookup"><span data-stu-id="f8ed3-124">Deploying Ports and Assemblies</span></span>](../core/deploying-ports-and-assemblies4.md)