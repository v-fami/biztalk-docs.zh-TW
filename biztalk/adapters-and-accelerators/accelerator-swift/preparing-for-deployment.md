---
title: 準備部署 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, planning
ms.assetid: 437caa31-f7f8-42e0-af1f-13aaee0955cd
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c24a3404a5ea6a35269cd29ae792a46034a69f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22213942"
---
# <a name="preparing-for-deployment"></a><span data-ttu-id="9e3b8-102">準備部署</span><span class="sxs-lookup"><span data-stu-id="9e3b8-102">Preparing for Deployment</span></span>
<span data-ttu-id="9e3b8-103">本節提供在部署計畫和準備工作階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-103">This section provides information about the planning and preparation phase of the deployment.</span></span> <span data-ttu-id="9e3b8-104">在實作之前部署，進行下列準備：</span><span class="sxs-lookup"><span data-stu-id="9e3b8-104">Before implementing a deployment, make the following preparations:</span></span>  
  
1.  <span data-ttu-id="9e3b8-105">閱讀並了解任何已知的問題，並準備設備：</span><span class="sxs-lookup"><span data-stu-id="9e3b8-105">Read and understand any known issues, and prepare the equipment:</span></span>  
  
    -   <span data-ttu-id="9e3b8-106">建立的硬體和軟體部署和網路圖表] 和 [部署工作表，以反映您變化 （根據網路圖表，並針對您選取的部署架構） 的部署所需的檢查清單。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-106">Create a checklist of the hardware and software required for your deployment, and a network diagram and deployment worksheet that reflect your variation of the deployment (based on the network diagram and for the deployment architecture you have selected).</span></span>  
  
    -   <span data-ttu-id="9e3b8-107">取得硬體與軟體在您的檢查清單。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-107">Acquire the hardware and software on your checklist.</span></span> <span data-ttu-id="9e3b8-108">此擷取包含所有的 service pack、 hotfix，與您部署所需的軟體更新的下載。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-108">This acquisition includes downloading all of the service packs, hotfixes, and software updates that are required for your deployment.</span></span>  
  
         <span data-ttu-id="9e3b8-109">下載使用的電腦具有網際網路存取這些軟體元件，然後將複製到 CD-ROM 更容易發佈這些軟體元件。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-109">Download these software components using a computer with Internet access and then copy these software components onto a CD-ROM for easier distribution.</span></span>  
  
2.  <span data-ttu-id="9e3b8-110">分隔成不同的階段部署，並識別每個階段相關聯的工作。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-110">Separate your deployment into different stages and identify the tasks associated with each stage.</span></span> <span data-ttu-id="9e3b8-111">這項策略組織根據特定部署階段工作，以簡化部署程序。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-111">This strategy simplifies the deployment process by organizing the tasks according to a specific deployment stage.</span></span> <span data-ttu-id="9e3b8-112">例如，規定的部署包含下列伺服器部署階段：</span><span class="sxs-lookup"><span data-stu-id="9e3b8-112">For example, the prescribed deployment includes the following server deployment stages:</span></span>  
  
3.  <span data-ttu-id="9e3b8-113">設定網域控制站。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-113">Configuring the domain controller.</span></span>  
  
4.  <span data-ttu-id="9e3b8-114">設定資料庫 (包括執行階段[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]叢集和設計階段的資料庫伺服器)。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-114">Configuring the databases (including the run-time [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] cluster and design-time database server).</span></span>  
  
5.  <span data-ttu-id="9e3b8-115">設定 BizTalk server。</span><span class="sxs-lookup"><span data-stu-id="9e3b8-115">Configuring the BizTalk servers.</span></span>  
  
 <span data-ttu-id="9e3b8-116">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="9e3b8-116">This section contains:</span></span>  
  
-   [<span data-ttu-id="9e3b8-117">網路需求</span><span class="sxs-lookup"><span data-stu-id="9e3b8-117">Network Requirements</span></span>](../../adapters-and-accelerators/accelerator-swift/network-requirements.md)  
  
-   [<span data-ttu-id="9e3b8-118">硬體和軟體需求的部署</span><span class="sxs-lookup"><span data-stu-id="9e3b8-118">Hardware and Software Requirements for Deployment</span></span>](../../adapters-and-accelerators/accelerator-swift/hardware-and-software-requirements-for-deployment.md)