---
title: 手動設定 Siebel 配接器的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- physical port binding, manually configuring
- how to, manually configure adapters for sending messages to a Siebel system
ms.assetid: a1445b8a-440f-45e8-96e9-a13142ca87c6
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25afdeaf544cddb67440d050690ca8ca08df4547
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020030"
---
# <a name="manually-configure-a-physical-port-binding-to-the-siebel-adapter"></a><span data-ttu-id="b697f-102">手動設定 Siebel 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="b697f-102">Manually configure a physical port binding to the Siebel adapter</span></span>
<span data-ttu-id="b697f-103">本節提供設定的相關資訊[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]為 WCF 自訂繫結使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b697f-103">This section provides information about configuring the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] as a WCF custom binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="b697f-104">在部署之後，配接器，您將能夠傳送和接收來自 Siebel 系統的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="b697f-104">After deploying the adapter, you will be able to send and receive messages from the Siebel system by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span> <span data-ttu-id="b697f-105">部署配接器的步驟而異的之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b697f-105">The steps for deploying the adapter vary depending on the direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="b697f-106">您可以選擇設定 傳送 或 傳送接收埠。</span><span class="sxs-lookup"><span data-stu-id="b697f-106">You may choose to configure a Send or a Send-Receive port.</span></span> <span data-ttu-id="b697f-107">您選擇的項目摘要如下表：</span><span class="sxs-lookup"><span data-stu-id="b697f-107">Your choices are summarized in the following table:</span></span>  
  
|<span data-ttu-id="b697f-108">連接埠方向</span><span class="sxs-lookup"><span data-stu-id="b697f-108">Port direction</span></span>|<span data-ttu-id="b697f-109">通訊模式</span><span class="sxs-lookup"><span data-stu-id="b697f-109">Communication pattern</span></span>|<span data-ttu-id="b697f-110">可從中選擇的通訊方向</span><span class="sxs-lookup"><span data-stu-id="b697f-110">Direction of communication to choose from</span></span>|  
|---|---|---|  
|<span data-ttu-id="b697f-111">Send</span><span class="sxs-lookup"><span data-stu-id="b697f-111">Send</span></span>|<span data-ttu-id="b697f-112">單向</span><span class="sxs-lookup"><span data-stu-id="b697f-112">One-way</span></span>|<span data-ttu-id="b697f-113">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b697f-113">I will always be sending messages on this port.</span></span>|  
|<span data-ttu-id="b697f-114">傳送-接收</span><span class="sxs-lookup"><span data-stu-id="b697f-114">Send-Receive</span></span>|<span data-ttu-id="b697f-115">要求-回應</span><span class="sxs-lookup"><span data-stu-id="b697f-115">Request-response</span></span>|<span data-ttu-id="b697f-116">我將會傳送要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="b697f-116">I will be sending a request and receiving a response.</span></span>|  
  
 <span data-ttu-id="b697f-117">如需詳細資訊，請參閱 <<c0> [ 建立和設定傳送埠](../../core/creating-and-configuring-send-ports.md)。</span><span class="sxs-lookup"><span data-stu-id="b697f-117">For more information, see [Creating and Configuring Send Ports](../../core/creating-and-configuring-send-ports.md).</span></span>
  
> [!NOTE]
>  <span data-ttu-id="b697f-118">收到不支援連接埠，因為[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]不會啟用來自 Siebel 系統的輸入的操作。</span><span class="sxs-lookup"><span data-stu-id="b697f-118">Receive ports are not supported because the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] does not enable inbound operations from the Siebel system.</span></span>  
> 
> [!NOTE]
>  <span data-ttu-id="b697f-119">您也可以藉由匯入所建立的繫結組態檔來設定 Wcf-custom 傳送埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中繼資料產生的一部分。</span><span class="sxs-lookup"><span data-stu-id="b697f-119">You can also configure the WCF-Custom send ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="b697f-120">如需有關設定連接埠使用此繫結檔案的指示，請參閱[設定的實體連接埠繫結使用的連接埠繫結檔案至 Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md)。</span><span class="sxs-lookup"><span data-stu-id="b697f-120">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to Siebel](../../adapters-and-accelerators/adapter-siebel/configure-a-physical-port-binding-using-a-port-binding-file-to-siebel.md).</span></span>
  
 
  
## <a name="see-also"></a><span data-ttu-id="b697f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b697f-121">See Also</span></span>  
[<span data-ttu-id="b697f-122">若要建立與 Siebel 配接器的 BizTalk 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="b697f-122">Building blocks to create BizTalk applications with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/building-blocks-to-create-biztalk-applications-with-the-siebel-adapter.md)