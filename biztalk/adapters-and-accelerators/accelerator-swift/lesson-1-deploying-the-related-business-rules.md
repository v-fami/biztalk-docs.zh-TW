---
title: "第 1 課： 部署相關的商務規則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, deploying
- deploying, business rules
ms.assetid: f8f5b103-4b66-4836-8165-99692574961a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 17c4b470b802a980306481361c1fafcec4f70269
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="lesson-1-deploying-the-related-business-rules"></a><span data-ttu-id="3b11c-102">第 1 課： 部署相關的商務規則</span><span class="sxs-lookup"><span data-stu-id="3b11c-102">Lesson 1: Deploying the Related Business Rules</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="3b11c-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]包含程式在 A4SWIFT 軟體開發套件 (SDK) 稱為 「 商務規則引擎 (BRE) 部署公用程式。</span><span class="sxs-lookup"><span data-stu-id="3b11c-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes a program in the A4SWIFT Software Development Kit (SDK) called the Business Rule Engine (BRE) Deployment Utility.</span></span> <span data-ttu-id="3b11c-104">在這一課，您可以使用此公用程式檢查組件以取得部署的結構描述、 決定所需的規則，及部署必要的詞彙和每個結構描述的原則。</span><span class="sxs-lookup"><span data-stu-id="3b11c-104">In this lesson, you use this utility to inspect an assembly for deployed schemas, determine the required rules, and deploy the necessary vocabularies and policies for each schema.</span></span>  
  
 <span data-ttu-id="3b11c-105">您也可以使用 SWIFT 標準發行指南 (SRG) 來識別所需的規則，然後使用商務規則編輯器 」 工具來部署的詞彙和原則部署的規則。</span><span class="sxs-lookup"><span data-stu-id="3b11c-105">You can also deploy rules by using the SWIFT Standards Release Guides (SRG) to identify the necessary rules and then use the Business Rule Composer tool to deploy the vocabularies and policies.</span></span>  
  
### <a name="to-deploy-the-related-business-rules"></a><span data-ttu-id="3b11c-106">若要部署的相關的商務規則</span><span class="sxs-lookup"><span data-stu-id="3b11c-106">To deploy the related business rules</span></span>  
  
1.  <span data-ttu-id="3b11c-107">按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**。</span><span class="sxs-lookup"><span data-stu-id="3b11c-107">Click **Start**, point to **Programs**, point to **Microsoft BizTalk \<version\> Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="3b11c-108">在 BRE 部署公用程式 對話方塊中，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="3b11c-108">In the BRE Deployment Utility dialog box, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="3b11c-109">在.NET 全域組件快取] 對話方塊中，選取**SWIFTSchemas**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="3b11c-109">In the .NET Global Assembly Cache dialog box, select **SWIFTSchemas**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3b11c-110">SWIFTSchemas 參考組件您先前部署。</span><span class="sxs-lookup"><span data-stu-id="3b11c-110">SWIFTSchemas refers to the assembly you previously deployed.</span></span>  
  
4.  <span data-ttu-id="3b11c-111">按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="3b11c-111">Click **Deploy**.</span></span>  
  
     <span data-ttu-id="3b11c-112">根據您部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行 BRE 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="3b11c-112">Based on the schemas you deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE.</span></span> <span data-ttu-id="3b11c-113">完成時，BRE 部署公用程式會顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="3b11c-113">When complete, the BRE Deployment Utility displays the following message:</span></span>  
  
     <span data-ttu-id="3b11c-114">**部署已完成。如需詳細資訊，檢視記錄檔或商務規則編輯器 」。**</span><span class="sxs-lookup"><span data-stu-id="3b11c-114">**Deployment has completed. View the log file or Business Rules Composer for details.**</span></span>  
  
5.  <span data-ttu-id="3b11c-115">關閉 SWIFT BRE 部署公用程式的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3b11c-115">Close the SWIFT BRE Deployment Utility dialog box.</span></span>  
  
6.  <span data-ttu-id="3b11c-116">在 Windows 檔案總管，瀏覽至\<*磁碟機*\>: \Documents and Settings\All Users\Application 資料，確認記錄檔**BREDeploymentLog.txt**會出現在資料夾。</span><span class="sxs-lookup"><span data-stu-id="3b11c-116">In Windows Explorer, browse to \<*drive*\>:\Documents and Settings\All Users\Application Data to confirm that the log file **BREDeploymentLog.txt** appears in the folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3b11c-117">您可以開啟記錄檔，以確認部署步驟的每個使用文字編輯器。</span><span class="sxs-lookup"><span data-stu-id="3b11c-117">You can open the log file using a text editor to confirm each of the deployment steps.</span></span>  
  
7.  <span data-ttu-id="3b11c-118">重新啟動 「 規則引擎更新服務。</span><span class="sxs-lookup"><span data-stu-id="3b11c-118">Restart the Rule Engine Update Service.</span></span> <span data-ttu-id="3b11c-119">這樣即可**啟動**，然後按一下**執行**、 輸入**services.msc**，然後按一下**[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3b11c-119">Do so by clicking **Start**, clicking **Run**, entering **services.msc**, and clicking **OK**.</span></span> <span data-ttu-id="3b11c-120">在**服務 （本機）**視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="3b11c-120">In the **Services (Local)** window, right-click **Rule Engine Update Service**, and then click **Restart**.</span></span>  
  
 <span data-ttu-id="3b11c-121">若要繼續[第 2 課： 確認部署使用 「 商務規則編輯器 」 工具](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="3b11c-121">Proceed to [Lesson 2: Confirming the Deployment Using the Business Rule Composer Tool](../../adapters-and-accelerators/accelerator-swift/lesson-2-confirming-the-deployment-using-the-business-rule-composer-tool.md).</span></span>