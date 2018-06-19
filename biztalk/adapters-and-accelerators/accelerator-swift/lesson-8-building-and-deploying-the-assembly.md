---
title: 第 8 課： 建立和部署組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- building assemblies
- deploying, assemblies
- assemblies, building
- assemblies, deploying
ms.assetid: 74c9dfbd-8365-4600-8885-a9d9c3490dd5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 607b3a304260e67a6640e579924705719ff8b850
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960916"
---
# <a name="lesson-8-building-and-deploying-the-assembly"></a><span data-ttu-id="6c1a1-102">第 8 課： 建立和部署組件</span><span class="sxs-lookup"><span data-stu-id="6c1a1-102">Lesson 8: Building and Deploying the Assembly</span></span>
<span data-ttu-id="6c1a1-103">在這一課，您可以建置及部署管線專案以產生包含您在上一個步驟中建立的管線的組件。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-103">In this lesson, you build and deploy the pipeline project to generate an assembly that contains the pipelines you created in the previous steps.</span></span> <span data-ttu-id="6c1a1-104">這一課中，可確保您目前已建立的工作中沒有編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-104">This lesson ensures there are no compilation errors in the work you have created so far.</span></span>  
  
 <span data-ttu-id="6c1a1-105">您的專案編譯成組件 (DLL) 檔案，並儲存在\<*磁碟機*\>: \Program Files\Microsoft BizTalk Accelerator for SWIFT\bin\Development 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-105">You compile the project into an assembly (DLL) file and save it in the \<*drive*\>:\Program Files\Microsoft BizTalk Accelerator for SWIFT\bin\Development folder.</span></span>  
  
### <a name="to-build-and-deploy-the-project"></a><span data-ttu-id="6c1a1-106">建置和部署專案</span><span class="sxs-lookup"><span data-stu-id="6c1a1-106">To build and deploy the project</span></span>  
  
1.  <span data-ttu-id="6c1a1-107">在 方案總管 中，以滑鼠右鍵按一下**SWIFTPipelines**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-107">In Solution Explorer, right-click **SWIFTPipelines**, and then click **Build**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c1a1-108">在編譯過程中，您應該不會看到任何失敗。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-108">During the compilation process, you should not see any failures.</span></span> <span data-ttu-id="6c1a1-109">如果您這樣做，請檢查錯誤的來源、 修正和重新建置專案。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-109">If you do, check the source of the error, correct it and then re-build the project.</span></span> <span data-ttu-id="6c1a1-110">不過，您可能看到 A4SWIFT 管線元件相關的警告數目。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-110">You may, however, see a number of warnings related to the A4SWIFT pipeline components.</span></span> <span data-ttu-id="6c1a1-111">您可以修正導致藉由設定這些警告的狀況**複製到本機**屬性的管線元件參考**False**。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-111">You can correct the condition leading to these warnings by setting the **Copy Local** properties of the pipeline component references to **False**.</span></span> <span data-ttu-id="6c1a1-112">如需詳細資訊，請參閱 「 建置管線專案可能會導致警告 」，在[其他已知問題](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6)。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-112">For more information, see "Building a pipeline project may result in warnings" in [Miscellaneous Known Issues](http://msdn.microsoft.com/library/bc94c781-2a56-4f80-8ecb-e654de2f6ed6).</span></span>  
  
2.  <span data-ttu-id="6c1a1-113">若要確認是否已建立 SWIFTPipelines.dll 檔案，使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管 中，瀏覽至\<*磁碟機*:\>\labs\SWIFTProject\SWIFTPipelines\bin\Development，並確定該檔案位於這個資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-113">To verify the creation of the SWIFTPipelines.dll file, using [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, browse to \<*drive*:\>\labs\SWIFTProject\SWIFTPipelines\bin\Development, and ensure that the file exists in this folder.</span></span>  
  
3.  <span data-ttu-id="6c1a1-114">在 方案總管 中，以滑鼠右鍵按一下**SWIFTPipelines**，然後按一下 **部署**。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-114">In Solution Explorer, right-click **SWIFTPipelines**, and then click **Deploy**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6c1a1-115">在部署過程中，您應該不會看到任何錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-115">During the deployment process, you should not see any failures or warnings.</span></span> <span data-ttu-id="6c1a1-116">如果您這樣做，請檢查錯誤的來源、 更正它，和重新部署專案。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-116">If you do, check the source of the error, correct it, and then re-deploy the project.</span></span>  
  
4.  <span data-ttu-id="6c1a1-117">若要符合在部署成功**檢視**功能表[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]，按一下  **BizTalk 總管**。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-117">To conform deployment success, in the **View** menu of [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], click **BizTalk Explorer**.</span></span>  
  
5.  <span data-ttu-id="6c1a1-118">以滑鼠右鍵按一下**BizTalk 組態資料庫**，然後按一下 **重新整理**。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-118">Right-click **BizTalk Configuration Databases**, and then click **Refresh**.</span></span>  
  
6.  <span data-ttu-id="6c1a1-119">展開**組件**節點，並確認快速鍵成功部署**SWIFTPipelines (1.0.0.0)**。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-119">Expand the **Assemblies** node and confirm that the accelerator successfully deployed **SWIFTPipelines (1.0.0.0)**.</span></span>  
  
 <span data-ttu-id="6c1a1-120">若要繼續[模組 4： 建立 XML 接收和一般檔案傳送埠](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md)。</span><span class="sxs-lookup"><span data-stu-id="6c1a1-120">Proceed to [Module 4: Creating XML Receive and Flat File Send Ports](../../adapters-and-accelerators/accelerator-swift/module-4-adding-an-xml-receive-location-and-flat-file-send-port.md).</span></span>