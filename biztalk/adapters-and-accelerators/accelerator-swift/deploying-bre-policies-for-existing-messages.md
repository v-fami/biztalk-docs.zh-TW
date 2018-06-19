---
title: BRE 原則部署的現有訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 585c903d-ee44-4e92-8798-febb176367e3
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4cd094feabe1ba23a6a73c89aae3a1042b8f7fc9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965004"
---
# <a name="deploying-bre-policies-for-existing-messages"></a><span data-ttu-id="e4cc9-102">將 BRE 原則部署現有的訊息</span><span class="sxs-lookup"><span data-stu-id="e4cc9-102">Deploying BRE Policies for Existing Messages</span></span>
<span data-ttu-id="e4cc9-103">**若要部署的相關的商務規則：**</span><span class="sxs-lookup"><span data-stu-id="e4cc9-103">**To deploy the related business rules:**</span></span>  
  
1.  <span data-ttu-id="e4cc9-104">按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk Accelerator for SWIFT**，然後按一下  **BRE 部署公用程式**。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-104">Click **Start**, click **Programs**, click **Microsoft BizTalk Accelerator for SWIFT**, and then click **BRE Deployment Utility**.</span></span>  
  
2.  <span data-ttu-id="e4cc9-105">在 BRE 部署公用程式，按一下 **瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-105">In BRE Deployment Utility, click **Browse**.</span></span>  
  
3.  <span data-ttu-id="e4cc9-106">在.NET 全域組件快取] 對話方塊中，選取**SWIFT MX 結構描述**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-106">In the .NET Global Assembly Cache dialog box, select **SWIFT MX Schema**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="e4cc9-107">按一下**部署**。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-107">Click **Deploy**.</span></span>  
  
     <span data-ttu-id="e4cc9-108">根據部署與該組件的結構描述，部署公用程式會識別相關的規則，並將其發行 BRE 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-108">Based on the schemas deployed with that assembly, the deployment utility identifies the related rules and publishes them for use with the BRE.</span></span> <span data-ttu-id="e4cc9-109">完成時，BRE 部署公用程式會顯示下列訊息: 「 已完成部署。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-109">When complete, the BRE Deployment Utility displays the following message: "Deployment has completed.</span></span> <span data-ttu-id="e4cc9-110">檢視記錄檔或商務規則編輯器 」 以取得詳細資料。 」</span><span class="sxs-lookup"><span data-stu-id="e4cc9-110">View the log file or Business Rules Composer for details."</span></span>  
  
5.  <span data-ttu-id="e4cc9-111">關閉 SWIFT BRE 部署公用程式的對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-111">Close the SWIFT BRE Deployment Utility dialog box.</span></span>  
  
6.  <span data-ttu-id="e4cc9-112">在 Windows 檔案總管，瀏覽至*\<磁碟機\>*: \Documents and Settings\All Users\Application 資料，確認記錄檔 BREDeploymentLog.txt 顯示資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-112">In Windows Explorer, browse to *\<drive\>*:\Documents and Settings\All Users\Application Data to confirm that the log file BREDeploymentLog.txt appears in the folder.</span></span>  
  
7.  <span data-ttu-id="e4cc9-113">按一下**啟動**，按一下 **執行**，型別**services.msc**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-113">Click **Start**, click **Run**, type **services.msc**, and then click **OK**.</span></span> <span data-ttu-id="e4cc9-114">在 服務 （本機） 視窗中，以滑鼠右鍵按一下**規則引擎更新服務**，然後按一下 **重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="e4cc9-114">In the Services (Local) window, right-click **Rule Engine Update Service**, and then click **Restart**.</span></span>