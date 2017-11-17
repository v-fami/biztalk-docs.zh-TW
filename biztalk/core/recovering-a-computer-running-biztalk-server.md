---
title: "復原執行 BizTalk Server 的電腦 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a55af6d6-f11a-46e4-9b8e-0a1ca35998c4
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74d9234fa1d3a572afadcc8e8ba90dd4735eb5c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="recovering-a-computer-running-biztalk-server"></a><span data-ttu-id="93144-102">復原執行 BizTalk Server 的電腦</span><span class="sxs-lookup"><span data-stu-id="93144-102">Recovering a Computer Running BizTalk Server</span></span>
<span data-ttu-id="93144-103">若要復原執行 BizTalk Server 的電腦，您必須能夠存取 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93144-103">In order to recover a computer running BizTalk Server, you must be able to access the BizTalk Server databases.</span></span> <span data-ttu-id="93144-104">如果需要，請還原 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93144-104">If necessary, restore the BizTalk Server databases.</span></span> <span data-ttu-id="93144-105">此外，在復原執行 BizTalk Server 的電腦之前，您必須先重新安裝 BizTalk Server 及所有必要的元件。</span><span class="sxs-lookup"><span data-stu-id="93144-105">In addition, before you can recover the computer running BizTalk Server, you must reinstall BizTalk Server and all of the prerequisites.</span></span>  
  
 <span data-ttu-id="93144-106">這些步驟完成後，您才可以使用本節中的程序復原 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="93144-106">When these steps are complete, you can use the procedures in this section to recover your BizTalk server.</span></span> <span data-ttu-id="93144-107">復原 BizTalk Server 所需執行的程序取決於您所使用的版本。</span><span class="sxs-lookup"><span data-stu-id="93144-107">The procedures you must follow to recover BizTalk Server depend on the edition you are using.</span></span> <span data-ttu-id="93144-108">下表列出每個版本的必要程序。</span><span class="sxs-lookup"><span data-stu-id="93144-108">The following table lists the required procedures for each edition.</span></span>  
  
|<span data-ttu-id="93144-109">工作</span><span class="sxs-lookup"><span data-stu-id="93144-109">Task</span></span>|<span data-ttu-id="93144-110">Standard</span><span class="sxs-lookup"><span data-stu-id="93144-110">Standard</span></span>|<span data-ttu-id="93144-111">開發人員</span><span class="sxs-lookup"><span data-stu-id="93144-111">Developer</span></span>|<span data-ttu-id="93144-112">Enterprise</span><span class="sxs-lookup"><span data-stu-id="93144-112">Enterprise</span></span>|  
|----------|--------------|---------------|----------------|  
|<span data-ttu-id="93144-113">**如何還原憑證存放區**</span><span class="sxs-lookup"><span data-stu-id="93144-113">**How to Restore the Certificate Store**</span></span>|<span data-ttu-id="93144-114">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-114">**X**</span></span>|||  
|<span data-ttu-id="93144-115">**如何復原企業單一登入 (SSO)**</span><span class="sxs-lookup"><span data-stu-id="93144-115">**How to Recover Enterprise Single Sign-On (SSO)**</span></span>|<span data-ttu-id="93144-116">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-116">**X**</span></span>|<span data-ttu-id="93144-117">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-117">**X**</span></span>|<span data-ttu-id="93144-118">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-118">**X**</span></span>|  
|<span data-ttu-id="93144-119">**如何復原 BizTalk 群組**</span><span class="sxs-lookup"><span data-stu-id="93144-119">**How to Recover the BizTalk Group**</span></span>|<span data-ttu-id="93144-120">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-120">**X**</span></span>|<span data-ttu-id="93144-121">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-121">**X**</span></span>|<span data-ttu-id="93144-122">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-122">**X**</span></span>|  
|<span data-ttu-id="93144-123">**如何復原 BizTalk Server 組態**</span><span class="sxs-lookup"><span data-stu-id="93144-123">**How to Recover the BizTalk Server Configuration**</span></span>|<span data-ttu-id="93144-124">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-124">**X**</span></span>|<span data-ttu-id="93144-125">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-125">**X**</span></span>|<span data-ttu-id="93144-126">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-126">**X**</span></span>|  
|<span data-ttu-id="93144-127">**如何復原 BAM 警示**</span><span class="sxs-lookup"><span data-stu-id="93144-127">**How to Recover BAM Alerts**</span></span><br /><br /> <span data-ttu-id="93144-128">除非您使用 BAM，否則不需要執行此動作。</span><span class="sxs-lookup"><span data-stu-id="93144-128">Not required unless you're using BAM.</span></span>|<span data-ttu-id="93144-129">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-129">**X**</span></span>|<span data-ttu-id="93144-130">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-130">**X**</span></span>|<span data-ttu-id="93144-131">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-131">**X**</span></span>|  
|<span data-ttu-id="93144-132">**如何復原 BAM 入口網站**</span><span class="sxs-lookup"><span data-stu-id="93144-132">**How to Recover the BAM Portal**</span></span><br /><br /> <span data-ttu-id="93144-133">除非您使用 BAM，否則不需要執行此動作。</span><span class="sxs-lookup"><span data-stu-id="93144-133">Not required unless you're using BAM.</span></span>|<span data-ttu-id="93144-134">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-134">**X**</span></span>|<span data-ttu-id="93144-135">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-135">**X**</span></span>|<span data-ttu-id="93144-136">**X**</span><span class="sxs-lookup"><span data-stu-id="93144-136">**X**</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="93144-137">本節內容</span><span class="sxs-lookup"><span data-stu-id="93144-137">In This Section</span></span>  
  
-   [<span data-ttu-id="93144-138">如何還原憑證存放區</span><span class="sxs-lookup"><span data-stu-id="93144-138">How to Restore the Certificate Store</span></span>](../core/how-to-restore-the-certificate-store.md)  
  
-   [<span data-ttu-id="93144-139">如何復原企業單一登入</span><span class="sxs-lookup"><span data-stu-id="93144-139">How to Recover Enterprise Single Sign-On</span></span>](../core/how-to-recover-enterprise-single-sign-on.md)  
  
-   [<span data-ttu-id="93144-140">如何復原 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="93144-140">How to Recover the BizTalk Group</span></span>](../core/how-to-recover-the-biztalk-group.md)  
  
-   [<span data-ttu-id="93144-141">如何復原 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="93144-141">How to Recover the BizTalk Server Configuration</span></span>](../core/how-to-recover-the-biztalk-server-configuration.md)  
  
-   [<span data-ttu-id="93144-142">如何復原 BAM 警示</span><span class="sxs-lookup"><span data-stu-id="93144-142">How to Recover BAM Alerts</span></span>](../core/how-to-recover-bam-alerts.md)  
  
-   [<span data-ttu-id="93144-143">如何復原 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="93144-143">How to Recover the BAM Portal</span></span>](../core/how-to-recover-the-bam-portal.md)