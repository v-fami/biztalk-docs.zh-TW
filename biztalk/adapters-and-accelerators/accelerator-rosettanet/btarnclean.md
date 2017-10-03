---
title: "BtarnClean |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BtarnClean utility
- assemblies, undeploying
- BTARN, deleting artifacts
- orchestrations, unenlisting
- ports, stopping
- orchestrations, stopping
- ports, deleting
- BTARN, BtarnClean utility
ms.assetid: fbecbb88-9b18-4b4b-a286-0bfa783f2320
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26397001014dd1e4d6ad7139e040892c71e22754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="btarnclean"></a><span data-ttu-id="81e2d-102">BtarnClean</span><span class="sxs-lookup"><span data-stu-id="81e2d-102">BtarnClean</span></span>
<span data-ttu-id="81e2d-103">您可使用 BtarnClean 公用程式清除電腦的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 成品。</span><span class="sxs-lookup"><span data-stu-id="81e2d-103">You use the BtarnClean utility to clean [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] artifacts off a computer.</span></span> <span data-ttu-id="81e2d-104">這包含下列動作：</span><span class="sxs-lookup"><span data-stu-id="81e2d-104">This includes the following actions:</span></span>  
  
-   <span data-ttu-id="81e2d-105">停止和取消登錄所有的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 協調流程</span><span class="sxs-lookup"><span data-stu-id="81e2d-105">Stopping and unenlisting all the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] orchestrations</span></span>  
  
-   <span data-ttu-id="81e2d-106">停止和刪除所有關聯的連接埠</span><span class="sxs-lookup"><span data-stu-id="81e2d-106">Stopping and deleting all the associated ports</span></span>  
  
-   <span data-ttu-id="81e2d-107">解除部署所有的 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.BTARN.* 組件</span><span class="sxs-lookup"><span data-stu-id="81e2d-107">Undeploying all the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.BTARN.* assemblies</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="81e2d-108">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="81e2d-108">Location in SDK</span></span>  
 <span data-ttu-id="81e2d-109">\<*磁碟機*> files\ Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK</span><span class="sxs-lookup"><span data-stu-id="81e2d-109">\<*drive*>\Program Files\ Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK</span></span>  
  
## <a name="running-btarnclean"></a><span data-ttu-id="81e2d-110">執行 BtarnClean</span><span class="sxs-lookup"><span data-stu-id="81e2d-110">Running BtarnClean</span></span>  
  
#### <a name="to-run-btarnclean"></a><span data-ttu-id="81e2d-111">若要執行 BtarnClean</span><span class="sxs-lookup"><span data-stu-id="81e2d-111">To run BtarnClean</span></span>  
  
1.  <span data-ttu-id="81e2d-112">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="81e2d-112">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="81e2d-113">移至\<*磁碟機*> \ Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNet\SDK\\。</span><span class="sxs-lookup"><span data-stu-id="81e2d-113">Move to \<*drive*>\ Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\\.</span></span>  
  
3.  <span data-ttu-id="81e2d-114">在命令提示字元中，輸入**BtarnClean**，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="81e2d-114">At the command prompt, type **BtarnClean**, and then press ENTER.</span></span>  
  
     <span data-ttu-id="81e2d-115">此公用程式會提示您確認您想要繼續。</span><span class="sxs-lookup"><span data-stu-id="81e2d-115">The utility prompts you to verify that you want to continue.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81e2d-116">備註</span><span class="sxs-lookup"><span data-stu-id="81e2d-116">Remarks</span></span>  
 <span data-ttu-id="81e2d-117">如果您在具有相依於其他成品之 BizTalk 成品的電腦上執行 BtarnClean 公用程式，BtarnClean 就會指出它無法移除該成品。</span><span class="sxs-lookup"><span data-stu-id="81e2d-117">If you run the BtarnClean utility on a computer that has a BizTalk artifact that depends on other artifacts, BtarnClean will indicate that it cannot remove the artifact.</span></span> <span data-ttu-id="81e2d-118">此公用程式會讓該成品保留在原處，然後繼續移除其他成品。</span><span class="sxs-lookup"><span data-stu-id="81e2d-118">The utility will leave that artifact in place and continue to remove other artifacts.</span></span> <span data-ttu-id="81e2d-119">您可移除相依性，然後再執行一次該公用程式。</span><span class="sxs-lookup"><span data-stu-id="81e2d-119">You can remove dependencies, and then run the utility again.</span></span>  
  
 <span data-ttu-id="81e2d-120">如果您在屬於多電腦部署之一部分的電腦上執行 BtarnClean 公用程式，移除成品將影響該部署中的其他伺服器。</span><span class="sxs-lookup"><span data-stu-id="81e2d-120">If you run the BtarnClean utility on a computer that is part of a multi-computer deployment, removing the artifacts will affect the rest of the servers in that deployment.</span></span>  
  
 <span data-ttu-id="81e2d-121">如果您在存在開發人員建立的多個程序時執行 BtarnClean 公用程式，此公用程式將不會移除仍在使用中的程序。</span><span class="sxs-lookup"><span data-stu-id="81e2d-121">If you run the BtarnClean utility when multiple processes created by developers exist, the utility will not remove processes that are still in use.</span></span>  
  
 <span data-ttu-id="81e2d-122">如果某個使用者的成品使用了主要接收位置，BtarnClean 公用程式將不會移除該接收位置。</span><span class="sxs-lookup"><span data-stu-id="81e2d-122">The BtarnClean utility will not remove a primary receive location if a user's artifact uses that receive location.</span></span> <span data-ttu-id="81e2d-123">在此情況下，您必須刪除接收埠。</span><span class="sxs-lookup"><span data-stu-id="81e2d-123">If this is the case, you must delete the receive port.</span></span>  
  
 <span data-ttu-id="81e2d-124">如果您想在執行此公用程式後取消設定 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，請從 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 資料夾執行 Configuration.exe /u。</span><span class="sxs-lookup"><span data-stu-id="81e2d-124">If you want to unconfigure [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] after running the utility, run Configuration.exe /u from the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e2d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e2d-125">See Also</span></span>  
 [<span data-ttu-id="81e2d-126">公用程式</span><span class="sxs-lookup"><span data-stu-id="81e2d-126">Utilities</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)