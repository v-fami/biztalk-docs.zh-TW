---
title: 準備部署 |Microsoft Docs
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
ms.openlocfilehash: 4d7b6f0677b542ad03b2109eddb3352924f6b59c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966495"
---
# <a name="preparing-for-deployment"></a><span data-ttu-id="c88f0-102">準備部署</span><span class="sxs-lookup"><span data-stu-id="c88f0-102">Preparing for Deployment</span></span>
<span data-ttu-id="c88f0-103">本節提供部署的規劃和準備階段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c88f0-103">This section provides information about the planning and preparation phase of the deployment.</span></span> <span data-ttu-id="c88f0-104">實作部署之前做好下列準備：</span><span class="sxs-lookup"><span data-stu-id="c88f0-104">Before implementing a deployment, make the following preparations:</span></span>  
  
1. <span data-ttu-id="c88f0-105">閱讀並了解任何已知的問題，然後準備設備：</span><span class="sxs-lookup"><span data-stu-id="c88f0-105">Read and understand any known issues, and prepare the equipment:</span></span>  
  
   -   <span data-ttu-id="c88f0-106">建立一份執行的硬體和軟體所需的部署，並反映您的部署 （根據網路圖表並針對您所選取的部署架構） 的變化的網路圖表] 和 [部署工作表。</span><span class="sxs-lookup"><span data-stu-id="c88f0-106">Create a checklist of the hardware and software required for your deployment, and a network diagram and deployment worksheet that reflect your variation of the deployment (based on the network diagram and for the deployment architecture you have selected).</span></span>  
  
   -   <span data-ttu-id="c88f0-107">取得的硬體和軟體，在您的檢查清單。</span><span class="sxs-lookup"><span data-stu-id="c88f0-107">Acquire the hardware and software on your checklist.</span></span> <span data-ttu-id="c88f0-108">此擷取包含所有的 service pack、 hotfix 與您的部署所需的軟體更新下載。</span><span class="sxs-lookup"><span data-stu-id="c88f0-108">This acquisition includes downloading all of the service packs, hotfixes, and software updates that are required for your deployment.</span></span>  
  
        <span data-ttu-id="c88f0-109">下載使用的電腦具有網際網路存取這些軟體元件，並複製到 CD-ROM 更容易散發這些軟體元件。</span><span class="sxs-lookup"><span data-stu-id="c88f0-109">Download these software components using a computer with Internet access and then copy these software components onto a CD-ROM for easier distribution.</span></span>  
  
2. <span data-ttu-id="c88f0-110">分隔成不同的階段部署，並識別每個階段相關聯的工作。</span><span class="sxs-lookup"><span data-stu-id="c88f0-110">Separate your deployment into different stages and identify the tasks associated with each stage.</span></span> <span data-ttu-id="c88f0-111">這項策略可簡化部署程序，藉由組織依據特定部署階段的工作。</span><span class="sxs-lookup"><span data-stu-id="c88f0-111">This strategy simplifies the deployment process by organizing the tasks according to a specific deployment stage.</span></span> <span data-ttu-id="c88f0-112">例如，指定的部署包含下列伺服器部署階段：</span><span class="sxs-lookup"><span data-stu-id="c88f0-112">For example, the prescribed deployment includes the following server deployment stages:</span></span>  
  
3. <span data-ttu-id="c88f0-113">設定網域控制站。</span><span class="sxs-lookup"><span data-stu-id="c88f0-113">Configuring the domain controller.</span></span>  
  
4. <span data-ttu-id="c88f0-114">設定資料庫 (包括執行階段[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]叢集和設計階段的資料庫伺服器)。</span><span class="sxs-lookup"><span data-stu-id="c88f0-114">Configuring the databases (including the run-time [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] cluster and design-time database server).</span></span>  
  
5. <span data-ttu-id="c88f0-115">設定 BizTalk 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c88f0-115">Configuring the BizTalk servers.</span></span>  
  
   <span data-ttu-id="c88f0-116">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="c88f0-116">This section contains:</span></span>  
  
-   [<span data-ttu-id="c88f0-117">網路需求</span><span class="sxs-lookup"><span data-stu-id="c88f0-117">Network Requirements</span></span>](../../adapters-and-accelerators/accelerator-swift/network-requirements.md)  
  
-   [<span data-ttu-id="c88f0-118">部署的硬體和軟體需求</span><span class="sxs-lookup"><span data-stu-id="c88f0-118">Hardware and Software Requirements for Deployment</span></span>](../../adapters-and-accelerators/accelerator-swift/hardware-and-software-requirements-for-deployment.md)