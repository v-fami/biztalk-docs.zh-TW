---
title: "服務管理網路 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21469dad-6c64-470a-bd58-8309d789ce6c
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 741abaaa3042cb40f7043b25ce041bb84740f26a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="service-network-management"></a><span data-ttu-id="e83ad-102">服務的網路管理</span><span class="sxs-lookup"><span data-stu-id="e83ad-102">Service Network Management</span></span>
<span data-ttu-id="e83ad-103">有效的執行階段管理需要的服務部署到執行階段環境的知識。</span><span class="sxs-lookup"><span data-stu-id="e83ad-103">Effective run-time governance requires knowledge of the services deployed into the run-time environment.</span></span> <span data-ttu-id="e83ad-104">AmberPoint SMS 可以探索的實際的接收位置和傳送埠在 BizTalk 管理群組中，部署，如圖 1 所示。</span><span class="sxs-lookup"><span data-stu-id="e83ad-104">AmberPoint SMS can discover the actual receive locations and send ports deployed within a BizTalk Management Group, as shown in Figure 1.</span></span>  
  
 <span data-ttu-id="e83ad-105">![AmberPoint 容器探索](../esb-toolkit/media/ch9-amberpointcontainerdiscovery.gif "Ch9 AmberPointContainerDiscovery")</span><span class="sxs-lookup"><span data-stu-id="e83ad-105">![AmberPoint Container Discovery](../esb-toolkit/media/ch9-amberpointcontainerdiscovery.gif "Ch9-AmberPointContainerDiscovery")</span></span>  
  
 <span data-ttu-id="e83ad-106">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="e83ad-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="e83ad-107">**AmberPoint SMS 容器探索螢幕**</span><span class="sxs-lookup"><span data-stu-id="e83ad-107">**The AmberPoint SMS Container Discovery screens**</span></span>  
  
 <span data-ttu-id="e83ad-108">使用上已部署的服務資訊，提供可幫助使用者了解執行階段組態並樂於上執行的其他服務及其相依性服務的各種不同觀點 AmberPoint SMS 服務網路。</span><span class="sxs-lookup"><span data-stu-id="e83ad-108">Using information on the deployed services, AmberPoint SMS presents various perspectives of the services that help users to understand the run-time configuration and appreciate their dependencies on other services within the running service network.</span></span> <span data-ttu-id="e83ad-109">圖 2 顯示的服務設定檔和相依性的畫面。</span><span class="sxs-lookup"><span data-stu-id="e83ad-109">Figure 2 shows the service profile and dependencies screens.</span></span>  
  
 <span data-ttu-id="e83ad-110">![AmberPoint 服務設定檔](../esb-toolkit/media/ch9-amberpointserviceprofile.gif "Ch9 AmberPointServiceProfile")</span><span class="sxs-lookup"><span data-stu-id="e83ad-110">![AmberPoint Service Profile](../esb-toolkit/media/ch9-amberpointserviceprofile.gif "Ch9-AmberPointServiceProfile")</span></span>  
  
 <span data-ttu-id="e83ad-111">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="e83ad-111">**Figure 2**</span></span>  
  
 <span data-ttu-id="e83ad-112">**AmberPoint SMS 服務設定檔和相依性螢幕**</span><span class="sxs-lookup"><span data-stu-id="e83ad-112">**The AmberPoint SMS service profile and dependencies screens**</span></span>  
  
 <span data-ttu-id="e83ad-113">AmberPoint SMS 可以發佈和轉送服務探索和執行階段中繼資料到現有的通用描述、 探索和整合 (UDDI) 登錄、 自訂組態管理的儲存機制，與主要系統管理主控台，例如Microsoft Operations Manager (MOM) 2004年和 System Center Operations Manager 2007 (SCOM)。</span><span class="sxs-lookup"><span data-stu-id="e83ad-113">AmberPoint SMS can publish and forward service discoveries and run-time metadata to existing Universal Description, Discovery, and Integration (UDDI) registries, custom configuration management repositories, and master system management consoles, such as Microsoft Operations Manager 2004 (MOM) and System Center Operations Manager 2007 (SCOM).</span></span>