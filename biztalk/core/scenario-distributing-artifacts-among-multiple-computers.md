---
title: "案例： 分配給多部電腦間的成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying [artifacts], multiple computers
- examples, distributing
- examples, artifacts
- artifacts, distributing
- artifacts, examples
- deploying [artifacts], examples
- examples, deploying
ms.assetid: 7000cded-1fda-4276-b7f3-3f427f686f64
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abedc60ad13c7e8b2be3ce4caa7b8d34262b4e5c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-distributing-artifacts-among-multiple-computers"></a><span data-ttu-id="1bc52-102">案例： 分配給多部電腦間的成品</span><span class="sxs-lookup"><span data-stu-id="1bc52-102">Scenario: Distributing Artifacts Among Multiple Computers</span></span>
<span data-ttu-id="1bc52-103">本主題說明如何將應用程式中的成品選擇性安裝在不同電腦的應用程式部署案例。</span><span class="sxs-lookup"><span data-stu-id="1bc52-103">This topic describes the application deployment scenario when the artifacts in an application are selectively installed on different computers.</span></span> <span data-ttu-id="1bc52-104">如果您要應用程式中的特定組件或其他類型的成品只安裝在 BizTalk 群組中的特定電腦上，可以這樣做。</span><span class="sxs-lookup"><span data-stu-id="1bc52-104">You might want to do this if you want certain assemblies or other types of artifacts in an application to be installed only on specific computers in a BizTalk group.</span></span> <span data-ttu-id="1bc52-105">若要執行這項作業，您可以根據要一起安裝在實體電腦上的成品，將應用程式中包含的成品匯出至多個 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc52-105">To do this, you can export the artifacts included in an application into multiple .msi files, according to which artifacts you want to install together on a physical computer.</span></span>  
  
 <span data-ttu-id="1bc52-106">下圖顯示 BizTalk 群組 1 匯入至 BizTalk 管理資料庫的.msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc52-106">The following diagram shows an .msi file that is imported into the BizTalk Management database for BizTalk Group 1.</span></span> <span data-ttu-id="1bc52-107">這會建立訂單處理應用程式和其所有的成品，該群組中。</span><span class="sxs-lookup"><span data-stu-id="1bc52-107">This creates the Order Processing application and all of its artifacts in that group.</span></span> <span data-ttu-id="1bc52-108">接著將應用程式成品匯出至兩個不同的 .msi 檔案。</span><span class="sxs-lookup"><span data-stu-id="1bc52-108">The application artifacts are then exported into two different .msi files.</span></span> <span data-ttu-id="1bc52-109">其中一個 .msi 檔案包含 Assembly1、Certificate1 和 Script1。</span><span class="sxs-lookup"><span data-stu-id="1bc52-109">One .msi file contains Assembly1, Certificate1, and Script1.</span></span> <span data-ttu-id="1bc52-110">另一個 .msi 檔案包含 Assembly2、Script2 和 VirtualDirectory1。</span><span class="sxs-lookup"><span data-stu-id="1bc52-110">The other .msi file contains Assembly2, Script2, and VirtualDirectory1.</span></span>  
  
 <span data-ttu-id="1bc52-111">這兩個.msi 檔案匯入 BizTalk 群組 2。</span><span class="sxs-lookup"><span data-stu-id="1bc52-111">Both .msi files are imported into BizTalk Group 2.</span></span> <span data-ttu-id="1bc52-112">因為它們都屬於訂單處理應用程式時，所有的這兩個.msi 檔案中的成品會匯入新的群組中名為訂單處理相同的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1bc52-112">Because they both belong to the Order Processing application, all of the artifacts in both .msi files are imported into the same application named Order Processing in the new group.</span></span>  
  
 <span data-ttu-id="1bc52-113">此外，應用程式成品會從 .msi 檔案安裝在群組中將執行這些成品的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1bc52-113">In addition, the application artifacts are installed from the .msi files onto the computers in the group that will run them.</span></span> <span data-ttu-id="1bc52-114">請注意，包含虛擬目錄的 .msi 檔案會安裝在 BizTalk Server B 和 BizTalk Server C，這兩個伺服器都是執行 IIS。</span><span class="sxs-lookup"><span data-stu-id="1bc52-114">Note that the .msi file containing the virtual directory is installed on BizTalk Server B and BizTalk Server C, which are both running IIS.</span></span>  
  
 <span data-ttu-id="1bc52-115">![安裝在不同電腦上的成品](../core/media/distributionofartifacts.gif "DistributionOfArtifacts")</span><span class="sxs-lookup"><span data-stu-id="1bc52-115">![Artifacts installed on different computers](../core/media/distributionofartifacts.gif "DistributionOfArtifacts")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc52-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc52-116">See Also</span></span>  
 <span data-ttu-id="1bc52-117">[應用程式部署和管理案例](../core/application-deployment-and-management-scenarios.md) </span><span class="sxs-lookup"><span data-stu-id="1bc52-117">[Application Deployment and Management Scenarios](../core/application-deployment-and-management-scenarios.md) </span></span>  
 <span data-ttu-id="1bc52-118">[如何匯出 BizTalk 應用程式](../core/how-to-export-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="1bc52-118">[How to Export a BizTalk Application](../core/how-to-export-a-biztalk-application.md) </span></span>  
 <span data-ttu-id="1bc52-119">[如何匯入 BizTalk 應用程式](../core/how-to-import-a-biztalk-application.md) </span><span class="sxs-lookup"><span data-stu-id="1bc52-119">[How to Import a BizTalk Application](../core/how-to-import-a-biztalk-application.md) </span></span>  
 [<span data-ttu-id="1bc52-120">如何安裝 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="1bc52-120">How to Install a BizTalk Application</span></span>](../core/how-to-install-a-biztalk-application.md)