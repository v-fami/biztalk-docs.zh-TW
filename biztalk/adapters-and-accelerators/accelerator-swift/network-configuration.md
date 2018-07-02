---
title: 網路組態 |Microsoft Docs
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
ms.openlocfilehash: 8fb693b9718b7c92e24f3537bea7ef27267f9a05
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967439"
---
# <a name="network-configuration"></a><span data-ttu-id="a4203-102">網路組態</span><span class="sxs-lookup"><span data-stu-id="a4203-102">Network Configuration</span></span>
<span data-ttu-id="a4203-103">本節中的指引可用於在您的部署中設定網路。</span><span class="sxs-lookup"><span data-stu-id="a4203-103">This section provides prescriptive guidance for configuring the network in your deployment.</span></span> <span data-ttu-id="a4203-104">如需詳細資訊，請參閱 <<c0> [ 準備部署](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md)。</span><span class="sxs-lookup"><span data-stu-id="a4203-104">For more information, see [Preparing for Deployment](../../adapters-and-accelerators/accelerator-swift/preparing-for-deployment.md).</span></span>  

 <span data-ttu-id="a4203-105">您在參數中定義虛擬區域網路 (Vlan)，然後連接適當的纜線</span><span class="sxs-lookup"><span data-stu-id="a4203-105">You define virtual local area networks (VLANs) in the switch and then connect the appropriate cables.</span></span> <span data-ttu-id="a4203-106">藉由定義 Vlan，您會指定針對每個網路區段或層交換器連接埠。</span><span class="sxs-lookup"><span data-stu-id="a4203-106">By defining the VLANs, you are designating ports on the switch for each network segment or tier.</span></span> <span data-ttu-id="a4203-107">您必須建立 VLAN 的每個下列環境：</span><span class="sxs-lookup"><span data-stu-id="a4203-107">You must create a VLAN for each of the following environments:</span></span>  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4203-108"> 接收和傳送層</span><span class="sxs-lookup"><span data-stu-id="a4203-108"> receive and send tier</span></span>  

- [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="a4203-109"> 協調流程和資料庫層</span><span class="sxs-lookup"><span data-stu-id="a4203-109"> orchestration and database tier</span></span>  

- <span data-ttu-id="a4203-110">公司網路</span><span class="sxs-lookup"><span data-stu-id="a4203-110">Corporate network</span></span>  

  <span data-ttu-id="a4203-111">定義虛擬區域網路之後，您可以從伺服器連線的網路纜線到交換器上的適當連接埠。</span><span class="sxs-lookup"><span data-stu-id="a4203-111">After you have defined the VLANs, you can connect the network cables from the servers to the appropriate ports on the switch.</span></span>  

  <span data-ttu-id="a4203-112">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="a4203-112">This section contains:</span></span>  

- [<span data-ttu-id="a4203-113">實體圖表</span><span class="sxs-lookup"><span data-stu-id="a4203-113">Physical Diagram</span></span>](../../adapters-and-accelerators/accelerator-swift/physical-diagram.md)  

- [<span data-ttu-id="a4203-114">網路負載平衡</span><span class="sxs-lookup"><span data-stu-id="a4203-114">Network Load Balancing</span></span>](../../adapters-and-accelerators/accelerator-swift/network-load-balancing.md)
