---
title: 手動設定 Oracle E-business 配接器的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07369428-7b54-4d90-8c63-ba14e67fdbdd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 354b3937036e9cff832b3c0898ea1fa8d41c6377
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966679"
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter"></a><span data-ttu-id="ac798-102">手動設定 Oracle E-business 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="ac798-102">Manually configure a physical port binding to the Oracle E-Business adapter</span></span>
<span data-ttu-id="ac798-103">本節提供設定的相關資訊[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]為 WCF 自訂繫結或使用 Wcf-oracleebs 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac798-103">This section provides information about configuring the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] as a WCF custom binding or as a WCF-OracleEBS port by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ac798-104">部署之後，配接器，您將能夠傳送和接收 Oracle E-business Suite 中的訊息，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ac798-104">After deploying the adapter, you will be able to send and receive messages from Oracle E-Business Suite by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ac798-105">部署配接器的步驟而異：</span><span class="sxs-lookup"><span data-stu-id="ac798-105">The steps for deploying the adapter vary depending on:</span></span>  
  
- <span data-ttu-id="ac798-106">之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]而[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac798-106">The direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="ac798-107">您可以選擇設定傳送、 接收、 傳送-接收或接收-傳送埠。</span><span class="sxs-lookup"><span data-stu-id="ac798-107">You may choose to configure a send, receive, send-receive, or a receive-send port.</span></span> <span data-ttu-id="ac798-108">下表摘要說明您的選擇。</span><span class="sxs-lookup"><span data-stu-id="ac798-108">Your choices are summarized in the following table.</span></span>  
  
  |<span data-ttu-id="ac798-109">連接埠方向</span><span class="sxs-lookup"><span data-stu-id="ac798-109">Port direction</span></span>|<span data-ttu-id="ac798-110">通訊模式</span><span class="sxs-lookup"><span data-stu-id="ac798-110">Communication pattern</span></span>|<span data-ttu-id="ac798-111">可從中選擇的通訊方向</span><span class="sxs-lookup"><span data-stu-id="ac798-111">Direction of communication to choose from</span></span>|  
  |--------------------|---------------------------|-----------------------------------------------|  
  |<span data-ttu-id="ac798-112">Send</span><span class="sxs-lookup"><span data-stu-id="ac798-112">Send</span></span>|<span data-ttu-id="ac798-113">單向</span><span class="sxs-lookup"><span data-stu-id="ac798-113">One-way</span></span>|<span data-ttu-id="ac798-114">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="ac798-114">I will always be sending messages on this port.</span></span>|  
  |<span data-ttu-id="ac798-115">Receive</span><span class="sxs-lookup"><span data-stu-id="ac798-115">Receive</span></span>|<span data-ttu-id="ac798-116">單向</span><span class="sxs-lookup"><span data-stu-id="ac798-116">One-way</span></span>|<span data-ttu-id="ac798-117">我將總是在此連接埠接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ac798-117">I will always be receiving messages on this port.</span></span>|  
  |<span data-ttu-id="ac798-118">傳送接收</span><span class="sxs-lookup"><span data-stu-id="ac798-118">Send-receive</span></span>|<span data-ttu-id="ac798-119">要求-回應</span><span class="sxs-lookup"><span data-stu-id="ac798-119">Request-response</span></span>|<span data-ttu-id="ac798-120">我將會傳送要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="ac798-120">I will be sending a request and receiving a response.</span></span>|  
  |<span data-ttu-id="ac798-121">接收傳送</span><span class="sxs-lookup"><span data-stu-id="ac798-121">Receive-send</span></span>|<span data-ttu-id="ac798-122">請求-回應</span><span class="sxs-lookup"><span data-stu-id="ac798-122">Solicit-response</span></span>|<span data-ttu-id="ac798-123">我將會接收要求並傳送回應。</span><span class="sxs-lookup"><span data-stu-id="ac798-123">I will be receiving a request and sending a response.</span></span>|  
  
   <span data-ttu-id="ac798-124">如需詳細資訊，請參閱 <<c0> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 協助文件，網址[ http://go.microsoft.com/fwlink/?LinkID=101130 ](http://go.microsoft.com/fwlink/?LinkID=101130)。</span><span class="sxs-lookup"><span data-stu-id="ac798-124">For more information, see the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Help documentation at [http://go.microsoft.com/fwlink/?LinkID=101130](http://go.microsoft.com/fwlink/?LinkID=101130).</span></span>  
  
- <span data-ttu-id="ac798-125">是否將配接器傳送訊息，或從 Oracle E-business Suite 接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ac798-125">Whether the adapter sends messages to or receives messages from Oracle E-Business Suite.</span></span> <span data-ttu-id="ac798-126">根據您要傳送或接收訊息，您將會建立傳送或接收埠，分別。</span><span class="sxs-lookup"><span data-stu-id="ac798-126">Depending on whether you want to send or receive messages, you will create a send or receive port, respectively.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="ac798-127">您也可以設定傳送，或藉由匯入繫結組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中繼資料產生的一部分。</span><span class="sxs-lookup"><span data-stu-id="ac798-127">You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="ac798-128">如需有關設定連接埠使用此繫結檔案的指示，請參閱[設定實體的連接埠繫結使用的連接埠繫結檔案至 Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md)。</span><span class="sxs-lookup"><span data-stu-id="ac798-128">For instructions on configuring ports using this binding file, see [Configure a Physical Port Binding Using a Port Binding File to Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac798-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="ac798-129">In This Section</span></span>  
  
-   [<span data-ttu-id="ac798-130">設定連接埠使用 Wcf-custom 配接器和 Oracle E-business Suite</span><span class="sxs-lookup"><span data-stu-id="ac798-130">Configuring a Port Using the WCF-Custom Adapter and Oracle E-Business Suite</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-custom-adapter-and-oracle-e-business-suite.md)  
  
-   [<span data-ttu-id="ac798-131">設定使用 Wcf-oracleebs 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="ac798-131">Configuring a Port Using the WCF-OracleEBS Adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-oracleebs-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="ac798-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac798-132">See Also</span></span>  
 [<span data-ttu-id="ac798-133">若要建立 Oracle E-business Suite 應用程式的建置組塊</span><span class="sxs-lookup"><span data-stu-id="ac798-133">Building blocks to create Oracle E-Business Suite applications</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)