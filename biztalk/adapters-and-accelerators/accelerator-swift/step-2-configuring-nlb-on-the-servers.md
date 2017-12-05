---
title: "步驟 2： 設定伺服器上的 NLB |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Network Load Balancing
- configuring, NLB
- NLB
ms.assetid: 30b2f645-b495-49a5-852b-cf89d25fd2b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6d174ba336a94d44aaffdb2605542035304d9ff
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="step-2-configuring-nlb-on-the-servers"></a><span data-ttu-id="8300b-102">步驟 2： 在伺服器上設定 NLB</span><span class="sxs-lookup"><span data-stu-id="8300b-102">Step 2: Configuring NLB on the Servers</span></span>
<span data-ttu-id="8300b-103">您已安裝的基礎平台，並設定適當的網路設定的伺服器之後 (請參閱[步驟 1： 安裝基底平台](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md))，您可能需要啟用 BizTalk HTTP 前端伺服器和 BizTalk 上的負載平衡訊息的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8300b-103">After you have installed the base platform and configured the servers with the proper network settings (see [Step 1: Installing the Base Platform](../../adapters-and-accelerators/accelerator-swift/step-1-installing-the-base-platform.md)), you may need to enable load balancing on BizTalk HTTP front-end servers and the BizTalk Messaging servers.</span></span> <span data-ttu-id="8300b-104">只有當您擁有一個或多個 BizTalk HTTP 前端伺服器安裝在一或多個 BizTalk 傳訊的伺服器從另一部電腦上，則需要這個步驟。</span><span class="sxs-lookup"><span data-stu-id="8300b-104">This step is needed only if you have one or more BizTalk HTTP front-end servers installed on a separate computer from one or more BizTalk Messaging servers.</span></span>  
  
 <span data-ttu-id="8300b-105">負載平衡可確保高可用性的用戶端電腦 （MRSR 網站瀏覽是 Internet Explorer 使用者） 和 MRSR 伺服器，以及 MRSR 伺服器與訊息伺服器之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="8300b-105">Load balancing ensures high-availability communication between the client computers (Internet Explorer users browsing to the MRSR site) and the MRSR servers, and between the MRSR servers and the messaging servers.</span></span>  
  
 <span data-ttu-id="8300b-106">上的負載平衡**公用**HTTP 前端伺服器的介面，才能啟用內部網路使用者連線到這些電腦上的 IIS Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="8300b-106">Load balancing on the **Public** interfaces of the HTTP front-end servers is required to enable the Intranet users to connect to the IIS Web servers on these computers.</span></span> <span data-ttu-id="8300b-107">上的負載平衡**私人**HTTP 前端伺服器的介面，才能啟用連絡這些電腦上的 web 服務訊息的伺服器。</span><span class="sxs-lookup"><span data-stu-id="8300b-107">Load balancing on the **Private** interfaces of the HTTP front-end servers is required to enable the messaging servers to contact the web services on these computers.</span></span>  
  
 <span data-ttu-id="8300b-108">訊息在伺服器上，假設有兩部伺服器，設定負載平衡上**私人**網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="8300b-108">On the messaging servers, assuming there are two servers, configure load balancing on the **Private** network adapters.</span></span>  
  
 <span data-ttu-id="8300b-109">如需詳細資訊，請參閱 BizTalk Server 部署指南。</span><span class="sxs-lookup"><span data-stu-id="8300b-109">For more information, see the BizTalk Server Deployment Guide.</span></span>