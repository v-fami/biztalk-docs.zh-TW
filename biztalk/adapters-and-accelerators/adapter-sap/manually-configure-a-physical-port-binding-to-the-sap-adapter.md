---
title: 以手動方式設定 SAP 配接器的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deploying, sending messages to the SAP system
- physical port binding, manually configuring
- deploying, receiving messages from the SAP system
ms.assetid: c4f547aa-5514-4ca9-809b-d8d395de419c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14aea45a1032a2e01e9560d9ab47e85e75506836
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994607"
---
# <a name="manually-configure-a-physical-port-binding-to-the-sap-adapter"></a><span data-ttu-id="57200-102">以手動方式設定 SAP 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="57200-102">Manually configure a physical port binding to the SAP adapter</span></span>
<span data-ttu-id="57200-103">設定[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]為 WCF 自訂繫結使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="57200-103">Configure the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] as a WCF custom binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> 

## <a name="port-overview"></a><span data-ttu-id="57200-104">連接埠概觀</span><span class="sxs-lookup"><span data-stu-id="57200-104">Port overview</span></span>
<span data-ttu-id="57200-105">部署之後，配接器，您將能夠傳送和接收來自 SAP 系統的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="57200-105">After deploying the adapter, you will be able to send and receive messages from the SAP system by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="57200-106">部署配接器的步驟而異：</span><span class="sxs-lookup"><span data-stu-id="57200-106">The steps for deploying the adapter vary depending on:</span></span>  
  
- <span data-ttu-id="57200-107">之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="57200-107">The direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="57200-108">您可以選擇設定傳送、 接收、 傳送-接收 」 或 「 接收-傳送埠。</span><span class="sxs-lookup"><span data-stu-id="57200-108">You may choose to configure a Send, Receive, Send-Receive, or a Receive-Send port.</span></span> <span data-ttu-id="57200-109">您選擇的項目摘要如下表：</span><span class="sxs-lookup"><span data-stu-id="57200-109">Your choices are summarized in the following table:</span></span>  
  
  |<span data-ttu-id="57200-110">連接埠方向</span><span class="sxs-lookup"><span data-stu-id="57200-110">Port direction</span></span>|<span data-ttu-id="57200-111">通訊模式</span><span class="sxs-lookup"><span data-stu-id="57200-111">Communication pattern</span></span>|<span data-ttu-id="57200-112">可從中選擇的通訊方向</span><span class="sxs-lookup"><span data-stu-id="57200-112">Direction of communication to choose from</span></span>|  
  |---|---|---|  
  |<span data-ttu-id="57200-113">Send</span><span class="sxs-lookup"><span data-stu-id="57200-113">Send</span></span>|<span data-ttu-id="57200-114">單向</span><span class="sxs-lookup"><span data-stu-id="57200-114">One-way</span></span>|<span data-ttu-id="57200-115">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="57200-115">I will always be sending messages on this port.</span></span>|  
  |<span data-ttu-id="57200-116">Receive</span><span class="sxs-lookup"><span data-stu-id="57200-116">Receive</span></span>|<span data-ttu-id="57200-117">單向</span><span class="sxs-lookup"><span data-stu-id="57200-117">One-way</span></span>|<span data-ttu-id="57200-118">我將總是在此連接埠接收訊息。</span><span class="sxs-lookup"><span data-stu-id="57200-118">I will always be receiving messages on this port.</span></span>|  
  |<span data-ttu-id="57200-119">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="57200-119">Send-Receive</span></span>|<span data-ttu-id="57200-120">要求-回應</span><span class="sxs-lookup"><span data-stu-id="57200-120">Request-response</span></span>|<span data-ttu-id="57200-121">我將會傳送要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="57200-121">I will be sending a request and receiving a response.</span></span>|  
  |<span data-ttu-id="57200-122">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="57200-122">Receive-Send</span></span>|<span data-ttu-id="57200-123">請求-回應</span><span class="sxs-lookup"><span data-stu-id="57200-123">Solicit-response</span></span>|<span data-ttu-id="57200-124">我將會接收要求並傳送回應。</span><span class="sxs-lookup"><span data-stu-id="57200-124">I will be receiving a request and sending a response.</span></span>|  
  
   <span data-ttu-id="57200-125">如需詳細資訊，請參閱 <<c0> [ 建立傳送埠](../../core/how-to-create-a-send-port2.md)，或[建立接收埠](../../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="57200-125">For more information, see [Create a Send Port](../../core/how-to-create-a-send-port2.md), or [Create a Receive Port](../../core/how-to-create-a-receive-port.md).</span></span>
  
- <span data-ttu-id="57200-126">無論配接器將訊息傳送至 SAP 系統，或從 SAP 系統接收訊息。</span><span class="sxs-lookup"><span data-stu-id="57200-126">Whether the adapter sends messages to the SAP system or receives messages from the SAP system.</span></span> <span data-ttu-id="57200-127">根據您要傳送或接收訊息，您將會建立傳送或接收埠。</span><span class="sxs-lookup"><span data-stu-id="57200-127">Depending on whether you want to send or receive messages, you will create a send or receive port.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="57200-128">您也可以設定傳送，或藉由匯入繫結組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中繼資料產生的一部分。</span><span class="sxs-lookup"><span data-stu-id="57200-128">You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="57200-129">如需有關設定連接埠使用此繫結檔案的指示，請參閱[設定的實體連接埠繫結使用的連接埠繫結檔案至 SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)。</span><span class="sxs-lookup"><span data-stu-id="57200-129">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="57200-130">本節內容</span><span class="sxs-lookup"><span data-stu-id="57200-130">In this section</span></span>  
  
-   [<span data-ttu-id="57200-131">設定使用 wcf-custom 配接器和 Oracle 資料庫配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="57200-131">Configure a port using the WCF-custom adapter and Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/configure-a-port-using-the-wcf-custom-adapter-and-oracle-database-adapter.md)  
  
-   [<span data-ttu-id="57200-132">使用 WCF-SAP 配接器設定連接埠</span><span class="sxs-lookup"><span data-stu-id="57200-132">Configure a port using the WCF-SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/configure-a-port-using-the-wcf-sap-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="57200-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57200-133">See Also</span></span>  
[<span data-ttu-id="57200-134">建立 SAP 應用程式的建構元素</span><span class="sxs-lookup"><span data-stu-id="57200-134">Building blocks to create SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md)