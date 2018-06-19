---
title: BizTalk ESB 工具組範例應用程式 |Microsoft 文件
description: 安裝 ESB Toolkit 範例應用程式，並取得有關如何在 BizTalk Server 中使用它們的快速連結
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 188f8e1f-26fb-4ea6-8e2e-f2ae3e46ca20
ms.author: mandia
ms.openlocfilehash: f9d1af5c2bc8c16ec14f8e13109f0edfe13b86cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290686"
---
# <a name="biztalk-esb-toolkit-sample-applications"></a><span data-ttu-id="097eb-103">BizTalk ESB 工具組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="097eb-103">BizTalk ESB Toolkit Sample Applications</span></span>
<span data-ttu-id="097eb-104">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例應用程式，您可以安裝和執行，以查看 ESB 運作，以及如何使用某些 ESB 管線元件。</span><span class="sxs-lookup"><span data-stu-id="097eb-104">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] includes several sample applications that you can install and run to see how the ESB works and how it uses some of the ESB pipeline components.</span></span> <span data-ttu-id="097eb-105">您可以調整，並修改程式碼和您自己的應用程式範例中所使用的技術。</span><span class="sxs-lookup"><span data-stu-id="097eb-105">You can adapt and modify the code and techniques used in the samples for your own applications.</span></span>  
  
## <a name="install-the-sample-applications"></a><span data-ttu-id="097eb-106">安裝範例應用程式</span><span class="sxs-lookup"><span data-stu-id="097eb-106">Install the sample applications</span></span>  
  
1.  <span data-ttu-id="097eb-107">建立名為 c： 磁碟機的根目錄中的專案的資料夾，並建立這個資料夾內名為 Microsoft.Practices.ESB 子資料夾。</span><span class="sxs-lookup"><span data-stu-id="097eb-107">Create a folder named Projects in the root of your C: drive, and create a subfolder named Microsoft.Practices.ESB within this folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="097eb-108">在目前版本中，支援的安裝是位於 C:\Projects\Microsoft.Practices.ESB 的資料夾中檔案的檔案。</span><span class="sxs-lookup"><span data-stu-id="097eb-108">In the current release, the supported installation is for the files to reside in the folder C:\Projects\Microsoft.Practices.ESB.</span></span> <span data-ttu-id="097eb-109">這些範例隨附的 BizTalk 繫結檔取決於這個路徑。</span><span class="sxs-lookup"><span data-stu-id="097eb-109">The BizTalk binding files that ship with the samples depend on this path.</span></span>  
  
2.  <span data-ttu-id="097eb-110">當您安裝[ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)，它包含在您指定的安裝位置中呼叫 ESBSource.zip.zip 檔案 (根據預設，C:\Program Files\\[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="097eb-110">When you install the [ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md), it includes a .zip file called ESBSource.zip in the installation location you specified (by default, C:\Program Files\\[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]).</span></span> <span data-ttu-id="097eb-111">程式 ESBSource.zip 檔案解壓縮到 C:\Projects\Microsoft.Practices.ESB 資料夾。</span><span class="sxs-lookup"><span data-stu-id="097eb-111">Uncompress the ESBSource.zip file into the C:\Projects\Microsoft.Practices.ESB folder.</span></span> <span data-ttu-id="097eb-112">這會建立名為的資料夾**金鑰**和**來源**其中包含範例金鑰和範例原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="097eb-112">This creates folders named **Keys** and **Source** that contain the sample key and the samples with source code.</span></span> <span data-ttu-id="097eb-113">來源資料夾中包含範例應用程式的原始程式碼，而且金鑰資料夾包含用來簽署組件中的範例應用程式的公用金鑰。</span><span class="sxs-lookup"><span data-stu-id="097eb-113">The Source folder contains the source code for the sample application, and the Keys folder contains the public keys used to sign the assemblies in the sample applications.</span></span>  
  
3.  <span data-ttu-id="097eb-114">執行範例之前，移除 C:\Projects\Microsoft.Practices.ESB\ 資料夾的唯讀屬性，以便正確地安裝範例。</span><span class="sxs-lookup"><span data-stu-id="097eb-114">Before you run the samples, remove the read-only attribute on the C:\Projects\Microsoft.Practices.ESB\ folder so that the samples install correctly.</span></span>  
  
4.  <span data-ttu-id="097eb-115">如果您不使用 PowerShell 指令碼之前，您必須以系統管理員身分開啟 PowerShell 並執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="097eb-115">If you have not used PowerShell scripts before, you must open PowerShell as an Administrator and run the following command:</span></span>  
  
    ```  
    set-executionpolicy unrestricted  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="097eb-116">如需 PowerShell 的詳細資訊，請參閱[Windows PowerShell 部落格](http://go.microsoft.com/fwlink/?LinkId=187593)([http://go.microsoft.com/fwlink/?LinkId = 187593](http://go.microsoft.com/fwlink/?LinkId=187593)) 和[Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([http://go.microsoft.com/fwlink/?LinkId = 187594](http://go.microsoft.com/fwlink/?LinkId=187594)) MSDN 上。</span><span class="sxs-lookup"><span data-stu-id="097eb-116">For more information about PowerShell, see the [Windows PowerShell Blog](http://go.microsoft.com/fwlink/?LinkId=187593) ([http://go.microsoft.com/fwlink/?LinkId=187593](http://go.microsoft.com/fwlink/?LinkId=187593)) and [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([http://go.microsoft.com/fwlink/?LinkId=187594](http://go.microsoft.com/fwlink/?LinkId=187594)) on MSDN.</span></span>  
  
5.  <span data-ttu-id="097eb-117">開啟以系統管理員命令提示字元並執行下列命令，以確保註冊 WCF 指令碼對應：</span><span class="sxs-lookup"><span data-stu-id="097eb-117">Open a command prompt as an administrator and run the following command to ensure WCF script maps are registered:</span></span>  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v3.0\Windows Communication Foundation>ServiceModelReg.exe -r -y  
    ```  
  
> [!NOTE]
>  <span data-ttu-id="097eb-118">您需要開啟 ESBSource.zip 檔案以取得範例程式碼存取。</span><span class="sxs-lookup"><span data-stu-id="097eb-118">You need to open the ESBSource.zip file in order to get an access to the Samples code.</span></span>  

## <a name="sample-applications"></a><span data-ttu-id="097eb-119">範例應用程式</span><span class="sxs-lookup"><span data-stu-id="097eb-119">Sample applications</span></span>  
 <span data-ttu-id="097eb-120">下列主題描述的範例應用程式，並包含額外的安裝指示，在適用情況：</span><span class="sxs-lookup"><span data-stu-id="097eb-120">The following topics describe the sample applications and include additional installation instructions where applicable:</span></span>  
  
-   [<span data-ttu-id="097eb-121">安裝例外狀況管理範例</span><span class="sxs-lookup"><span data-stu-id="097eb-121">Installing the Exception Management Samples</span></span>](../esb-toolkit/installing-the-exception-management-samples.md)  
  
-   [<span data-ttu-id="097eb-122">執行修復並重新送出的自訂例外狀況處理常式範例</span><span class="sxs-lookup"><span data-stu-id="097eb-122">Running the Repair and Resubmit Custom Exception Handler Sample</span></span>](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)  
  
-   [<span data-ttu-id="097eb-123">執行保存自訂例外狀況處理常式範例訊息</span><span class="sxs-lookup"><span data-stu-id="097eb-123">Running the Message Persisting Custom Exception Handler Sample</span></span>](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)  
  
-   [<span data-ttu-id="097eb-124">執行 BizTalk 失敗訊息路由 ESB 處理範例</span><span class="sxs-lookup"><span data-stu-id="097eb-124">Running the BizTalk Failed Message Routing ESB Processing Sample</span></span>](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)  
  
-   [<span data-ttu-id="097eb-125">安裝及執行路線上手範例</span><span class="sxs-lookup"><span data-stu-id="097eb-125">Installing and Running the Itinerary On-Ramp Sample</span></span>](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [<span data-ttu-id="097eb-126">安裝和執行 JMS MQRFH2 元件範例</span><span class="sxs-lookup"><span data-stu-id="097eb-126">Installing and Running the JMS MQRFH2 Component Sample</span></span>](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)  
  
-   [<span data-ttu-id="097eb-127">安裝及執行 「 命名空間元件 」 範例</span><span class="sxs-lookup"><span data-stu-id="097eb-127">Installing and Running the Namespace Component Sample</span></span>](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)  
  
-   [<span data-ttu-id="097eb-128">安裝及執行 「 轉換服務 」 範例</span><span class="sxs-lookup"><span data-stu-id="097eb-128">Installing and Running the Transformation Service Sample</span></span>](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)  
  
-   [<span data-ttu-id="097eb-129">安裝及執行動態解析範例</span><span class="sxs-lookup"><span data-stu-id="097eb-129">Installing and Running the Dynamic Resolution Sample</span></span>](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [<span data-ttu-id="097eb-130">安裝及執行 BizTalk 作業範例</span><span class="sxs-lookup"><span data-stu-id="097eb-130">Installing and Running the BizTalk Operations Sample</span></span>](../esb-toolkit/installing-and-running-the-biztalk-operations-sample.md)  
  
-   [<span data-ttu-id="097eb-131">安裝及執行解析程式服務範例</span><span class="sxs-lookup"><span data-stu-id="097eb-131">Installing and Running the Resolver Service Sample</span></span>](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)  
  
-   [<span data-ttu-id="097eb-132">安裝及執行分散-集中範例</span><span class="sxs-lookup"><span data-stu-id="097eb-132">Installing and Running the Scatter-Gather Sample</span></span>](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)  
  
-   [<span data-ttu-id="097eb-133">安裝及執行 「 訊息豐富 」 範例</span><span class="sxs-lookup"><span data-stu-id="097eb-133">Installing and Running the Message Enrichment Sample</span></span>](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md)  
  
-   [<span data-ttu-id="097eb-134">安裝及執行多個 Web 服務範例</span><span class="sxs-lookup"><span data-stu-id="097eb-134">Installing and Running the Multiple Web Services Sample</span></span>](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)  
  
-   [<span data-ttu-id="097eb-135">安裝及執行設計工具擴充性範例</span><span class="sxs-lookup"><span data-stu-id="097eb-135">Installing and Running the Designer Extensibility Sample</span></span>](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)  
  
-   [<span data-ttu-id="097eb-136">執行的例外狀況處理服務範例</span><span class="sxs-lookup"><span data-stu-id="097eb-136">Running the Exception Handling Service Sample</span></span>](../esb-toolkit/running-the-exception-handling-service-sample.md)