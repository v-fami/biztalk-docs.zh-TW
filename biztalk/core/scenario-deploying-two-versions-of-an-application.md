---
title: "案例： 部署兩個版本的應用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, multiple assemblies
- assemblies, multiple assemblies
- receive locations, examples
- assemblies, deploying
- assemblies, examples
ms.assetid: 3e79a7df-bf77-4a0b-86ec-359fcf3489b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1bb4f04e8b00dd171de89bbed6f01d2a2d1e2e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-deploying-two-versions-of-an-application"></a><span data-ttu-id="dcced-102">案例： 部署兩個版本的應用程式</span><span class="sxs-lookup"><span data-stu-id="dcced-102">Scenario: Deploying Two Versions of an Application</span></span>
<span data-ttu-id="dcced-103">本主題描述在 BizTalk 群組內部署兩個版本的應用程式，以便使其能同時執行的案例。</span><span class="sxs-lookup"><span data-stu-id="dcced-103">This topic describes the scenario of deploying two versions of an application within a BizTalk group, so that they can both run simultaneously.</span></span> <span data-ttu-id="dcced-104">在此案例中，您需要部署應用程式的主要新版本。</span><span class="sxs-lookup"><span data-stu-id="dcced-104">In this scenario, you need to deploy a major new version of the application.</span></span> <span data-ttu-id="dcced-105">由於結構描述或通訊協定的變更 (基本上是新的應用程式)，這項部署需要夥伴變更他們與系統進行的互動。</span><span class="sxs-lookup"><span data-stu-id="dcced-105">It requires partners to change their interaction with the system due to either schema or protocol change - essentially a new application.</span></span> <span data-ttu-id="dcced-106">對於此系統的改變已經通過測試，不過並沒有在完整規模的實際執行系統下測試過。</span><span class="sxs-lookup"><span data-stu-id="dcced-106">The changeover to this system has been tested but not under the scale of a full production system.</span></span> <span data-ttu-id="dcced-107">您要與 20% 的夥伴試驗新的系統，並且要逐漸增加該百分比，直到所有的夥伴都使用該系統為止。</span><span class="sxs-lookup"><span data-stu-id="dcced-107">You want to pilot the new system with 20 percent of the partners, and gradually increase that percentage until all the partners are using it.</span></span>  
  
 <span data-ttu-id="dcced-108">由於兩個應用程式會在兩個不同的接收位置接收訊息，您必須要求這些夥伴使用應用程式的新版本，將訊息傳送至新的 URL，如此它們才會由新版本處理。</span><span class="sxs-lookup"><span data-stu-id="dcced-108">Because the two applications receive messages on two different receive locations, you must ask those partners that should use the new version of the application to send messages to the new URL, so that they will be processed by the new version.</span></span>  
  
 <span data-ttu-id="dcced-109">下圖顯示典型的並存應用程式部署。</span><span class="sxs-lookup"><span data-stu-id="dcced-109">The following diagram shows a typical side-by-side application deployment.</span></span>  
  
 <span data-ttu-id="dcced-110">![部署在一起的兩個組件版本](../core/media/sidebysideassemblyversions.gif "SideBySideAssemblyVersions")</span><span class="sxs-lookup"><span data-stu-id="dcced-110">![Two Assembly Versions Deployed Together](../core/media/sidebysideassemblyversions.gif "SideBySideAssemblyVersions")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcced-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcced-111">See Also</span></span>  
 [<span data-ttu-id="dcced-112">應用程式部署和管理案例</span><span class="sxs-lookup"><span data-stu-id="dcced-112">Application Deployment and Management Scenarios</span></span>](../core/application-deployment-and-management-scenarios.md)