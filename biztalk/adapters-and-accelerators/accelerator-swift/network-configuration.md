---
title: 網路設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, network configuration
ms.assetid: fb6265b8-2e6d-4344-bb44-4f4fd995382d
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83a9e8ffe6b278c91429835c3ae32c96d45ef22e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22214422"
---
# <a name="network-configuration"></a><span data-ttu-id="52ee6-102">網路組態</span><span class="sxs-lookup"><span data-stu-id="52ee6-102">Network Configuration</span></span>
<span data-ttu-id="52ee6-103">本章節提供您的部署中設定網路的指引。</span><span class="sxs-lookup"><span data-stu-id="52ee6-103">This section provides prescriptive guidance for configuring the network in your deployment.</span></span> <span data-ttu-id="52ee6-104">如需詳細資訊，請參閱[準備部署](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="52ee6-104">For more information, see [Preparing for Deployment](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span></span>  
  
 <span data-ttu-id="52ee6-105">您定義在交換器的虛擬區域網路 (Vlan)，並連接適當的纜線，然後。</span><span class="sxs-lookup"><span data-stu-id="52ee6-105">You define virtual local area networks (VLANs) in the switch and then connect the appropriate cables.</span></span> <span data-ttu-id="52ee6-106">藉由定義 Vlan，您會指定針對每個網路區段或層交換器連接埠。</span><span class="sxs-lookup"><span data-stu-id="52ee6-106">By defining the VLANs, you are designating ports on the switch for each network segment or tier.</span></span> <span data-ttu-id="52ee6-107">您必須在下列環境的每個建立 VLAN:</span><span class="sxs-lookup"><span data-stu-id="52ee6-107">You must create a VLAN for each of the following environments:</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="52ee6-108">接收和傳送層</span><span class="sxs-lookup"><span data-stu-id="52ee6-108"> receive and send tier</span></span>  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="52ee6-109">協調流程和資料庫層</span><span class="sxs-lookup"><span data-stu-id="52ee6-109"> orchestration and database tier</span></span>  
  
-   <span data-ttu-id="52ee6-110">公司網路</span><span class="sxs-lookup"><span data-stu-id="52ee6-110">Corporate network</span></span>  
  
 <span data-ttu-id="52ee6-111">定義虛擬區域網路之後，您可以從伺服器連接的網路纜線到交換器上的適當連接埠。</span><span class="sxs-lookup"><span data-stu-id="52ee6-111">After you have defined the VLANs, you can connect the network cables from the servers to the appropriate ports on the switch.</span></span>  
  
 <span data-ttu-id="52ee6-112">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="52ee6-112">This section contains:</span></span>  
  
-   [<span data-ttu-id="52ee6-113">實體的圖表</span><span class="sxs-lookup"><span data-stu-id="52ee6-113">Physical Diagram</span></span>](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  
  
-   [<span data-ttu-id="52ee6-114">網路負載平衡</span><span class="sxs-lookup"><span data-stu-id="52ee6-114">Network Load Balancing</span></span>](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)