---
title: 手動設定 Oracle 資料庫配接器的實體連接埠繫結 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, sending to an Oracle database
- messages, receiving from an Oracle database
- physical port binding, manually configuring
ms.assetid: 6b118236-e9eb-494e-96b2-969c7064943d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79e002762175eb847385617e2efd570d342b1c3a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976201"
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-database-adapter"></a><span data-ttu-id="6060d-102">手動設定 Oracle 資料庫配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="6060d-102">Manually configure a physical port binding to the Oracle Database Adapter</span></span>
<span data-ttu-id="6060d-103">本節提供設定的相關資訊[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]做為 WCF 自訂繫結或使用 Wcf-oracledb 繫結[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6060d-103">This section provides information about configuring the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] as a WCF-Custom binding or WCF-OracleDB binding by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="6060d-104">部署之後，配接器，您將能夠傳送和接收訊息從 Oracle 資料庫，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="6060d-104">After deploying the adapter, you will be able to send and receive messages from the Oracle database by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="6060d-105">部署配接器的步驟而異：</span><span class="sxs-lookup"><span data-stu-id="6060d-105">The steps for deploying the adapter vary depending on:</span></span>  
  
- <span data-ttu-id="6060d-106">BizTalk Server 之間的通訊方向和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6060d-106">The direction of communication between BizTalk Server and [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="6060d-107">您可以選擇設定傳送、 接收、 傳送-接收或接收-傳送埠。</span><span class="sxs-lookup"><span data-stu-id="6060d-107">You may choose to configure a send, receive, send-receive, or a receive-send port.</span></span> <span data-ttu-id="6060d-108">下表摘要說明您的選擇。</span><span class="sxs-lookup"><span data-stu-id="6060d-108">Your choices are summarized in the following table.</span></span>  
  
  |<span data-ttu-id="6060d-109">連接埠方向</span><span class="sxs-lookup"><span data-stu-id="6060d-109">Port direction</span></span>|<span data-ttu-id="6060d-110">通訊模式</span><span class="sxs-lookup"><span data-stu-id="6060d-110">Communication pattern</span></span>|<span data-ttu-id="6060d-111">可從中選擇的通訊方向</span><span class="sxs-lookup"><span data-stu-id="6060d-111">Direction of communication to choose from</span></span>|  
  |--------------------|---------------------------|-----------------------------------------------|  
  |<span data-ttu-id="6060d-112">Send</span><span class="sxs-lookup"><span data-stu-id="6060d-112">Send</span></span>|<span data-ttu-id="6060d-113">單向</span><span class="sxs-lookup"><span data-stu-id="6060d-113">One-way</span></span>|<span data-ttu-id="6060d-114">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="6060d-114">I will always be sending messages on this port.</span></span>|  
  |<span data-ttu-id="6060d-115">Receive</span><span class="sxs-lookup"><span data-stu-id="6060d-115">Receive</span></span>|<span data-ttu-id="6060d-116">單向</span><span class="sxs-lookup"><span data-stu-id="6060d-116">One-way</span></span>|<span data-ttu-id="6060d-117">我將總是在此連接埠接收訊息。</span><span class="sxs-lookup"><span data-stu-id="6060d-117">I will always be receiving messages on this port.</span></span>|  
  |<span data-ttu-id="6060d-118">傳送接收</span><span class="sxs-lookup"><span data-stu-id="6060d-118">Send-receive</span></span>|<span data-ttu-id="6060d-119">要求-回應</span><span class="sxs-lookup"><span data-stu-id="6060d-119">Request-response</span></span>|<span data-ttu-id="6060d-120">我將會傳送要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="6060d-120">I will be sending a request and receiving a response.</span></span>|  
  |<span data-ttu-id="6060d-121">接收傳送</span><span class="sxs-lookup"><span data-stu-id="6060d-121">Receive-send</span></span>|<span data-ttu-id="6060d-122">請求-回應</span><span class="sxs-lookup"><span data-stu-id="6060d-122">Solicit-response</span></span>|<span data-ttu-id="6060d-123">我將會接收要求並傳送回應。</span><span class="sxs-lookup"><span data-stu-id="6060d-123">I will be receiving a request and sending a response.</span></span>|  
  
   <span data-ttu-id="6060d-124">如需詳細資訊，請參閱 <<c0> [ 建立傳送埠](../../core/how-to-create-a-send-port2.md)，或[建立接收埠](../../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="6060d-124">For more information, see [Create a Send Port](../../core/how-to-create-a-send-port2.md), or [Create a Receive Port](../../core/how-to-create-a-receive-port.md).</span></span> 
  
- <span data-ttu-id="6060d-125">無論配接器會將訊息傳送到 Oracle 資料庫，或從 Oracle 資料庫接收訊息。</span><span class="sxs-lookup"><span data-stu-id="6060d-125">Whether the adapter sends messages to the Oracle database or receives messages from the Oracle database.</span></span> <span data-ttu-id="6060d-126">根據您要傳送或接收訊息，您將會建立傳送或接收埠，分別。</span><span class="sxs-lookup"><span data-stu-id="6060d-126">Depending on whether you want to send or receive messages, you will create a send or receive port, respectively.</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="6060d-127">您也可以設定傳送，或藉由匯入繫結組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]中繼資料產生的一部分。</span><span class="sxs-lookup"><span data-stu-id="6060d-127">You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="6060d-128">如需有關設定連接埠使用此繫結檔案的指示，請參閱[設定為使用 Oracle 資料庫的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="6060d-128">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).</span></span>  
  
 
  
## <a name="see-also"></a><span data-ttu-id="6060d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6060d-129">See Also</span></span>  
[<span data-ttu-id="6060d-130">開發 BizTalk 應用程式</span><span class="sxs-lookup"><span data-stu-id="6060d-130">Develop your BizTalk applications</span></span>](../../core/develop-your-biztalk-applications.md)