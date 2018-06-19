---
title: 手動設定 SQL 配接器的實體連接埠繫結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d3f0bb78-c85f-4629-9e2d-cce180ff78ae
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac72d914539eabc9b129985c2b9335270e561d18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222662"
---
# <a name="manually-configure-a-physical-port-binding-to-the-sql-adapter"></a><span data-ttu-id="ef6f6-102">手動設定 SQL 配接器的實體連接埠繫結</span><span class="sxs-lookup"><span data-stu-id="ef6f6-102">Manually configure a physical port binding to the SQL adapter</span></span>
<span data-ttu-id="ef6f6-103">本節提供有關設定資訊[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]當作 WCF 自訂繫結或利用 WCF SQL 連接埠[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-103">This section provides information about configuring the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] as a WCF custom binding or as a WCF-SQL port by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ef6f6-104">部署之後，配接器，您將能夠傳送和接收訊息從 SQL Server，使用[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-104">After deploying the adapter, you will be able to send and receive messages from SQL Server by using the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ef6f6-105">部署配接器的步驟而異：</span><span class="sxs-lookup"><span data-stu-id="ef6f6-105">The steps for deploying the adapter vary depending on:</span></span>  
  
-   <span data-ttu-id="ef6f6-106">之間的通訊方向[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-106">The direction of communication between [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="ef6f6-107">您可以選擇設定傳送、 接收或傳送-接收埠。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-107">You may choose to configure a send, receive, or a send-receive port.</span></span> <span data-ttu-id="ef6f6-108">下表摘要說明您的選擇。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-108">Your choices are summarized in the following table.</span></span>  
  
    |<span data-ttu-id="ef6f6-109">連接埠方向</span><span class="sxs-lookup"><span data-stu-id="ef6f6-109">Port direction</span></span>|<span data-ttu-id="ef6f6-110">通訊模式</span><span class="sxs-lookup"><span data-stu-id="ef6f6-110">Communication pattern</span></span>|<span data-ttu-id="ef6f6-111">若要從選擇的通訊方向</span><span class="sxs-lookup"><span data-stu-id="ef6f6-111">Direction of communication to choose from</span></span>|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |<span data-ttu-id="ef6f6-112">Send</span><span class="sxs-lookup"><span data-stu-id="ef6f6-112">Send</span></span>|<span data-ttu-id="ef6f6-113">單向</span><span class="sxs-lookup"><span data-stu-id="ef6f6-113">One-way</span></span>|<span data-ttu-id="ef6f6-114">我將總是在此連接埠傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-114">I will always be sending messages on this port.</span></span>|  
    |<span data-ttu-id="ef6f6-115">Receive</span><span class="sxs-lookup"><span data-stu-id="ef6f6-115">Receive</span></span>|<span data-ttu-id="ef6f6-116">單向</span><span class="sxs-lookup"><span data-stu-id="ef6f6-116">One-way</span></span>|<span data-ttu-id="ef6f6-117">我將總是在此連接埠接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-117">I will always be receiving messages on this port.</span></span>|  
    |<span data-ttu-id="ef6f6-118">傳送接收</span><span class="sxs-lookup"><span data-stu-id="ef6f6-118">Send-receive</span></span>|<span data-ttu-id="ef6f6-119">要求-回應</span><span class="sxs-lookup"><span data-stu-id="ef6f6-119">Request-response</span></span>|<span data-ttu-id="ef6f6-120">我將會傳送要求並接收回應。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-120">I will be sending a request and receiving a response.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ef6f6-121">雙向接收埠不會受到[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-121">Two-way receive ports are not supported by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
     <span data-ttu-id="ef6f6-122">如需詳細資訊，請參閱[如何建立傳送埠](../../core/how-to-create-a-send-port2.md)，或[如何建立接收埠](../../core/how-to-create-a-receive-port.md)。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-122">For more information, see [How to Create a Send Port](../../core/how-to-create-a-send-port2.md), or [How to Create a Receive Port](../../core/how-to-create-a-receive-port.md).</span></span> 
  
-   <span data-ttu-id="ef6f6-123">無論配接器將訊息傳送至 SQL Server （輸出作業），或從 SQL Server （輸入操作） 接收訊息。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-123">Whether the adapter sends messages to the SQL Server (outbound operations) or receives messages from SQL Server (inbound operations).</span></span> <span data-ttu-id="ef6f6-124">根據您要傳送或接收訊息，您將會建立傳送或接收埠，分別。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-124">Depending on whether you want to send or receive messages, you will create a send or receive port, respectively.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef6f6-125">您也可以設定傳送，或藉由匯入繫結的組態檔所建立的接收埠[!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]做為中繼資料產生的一部分。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-125">You can also configure the send or receive ports by importing a binding configuration file that is created by the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] as part of metadata generation.</span></span> <span data-ttu-id="ef6f6-126">如需設定使用此繫結檔案的連接埠的指示，請參閱[設定要使用 SQL 配接器使用的連接埠繫結檔案的實體連接埠繫結](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="ef6f6-126">For instructions on configuring ports using this binding file, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="ef6f6-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="ef6f6-127">In This Section</span></span>  
  
-   [<span data-ttu-id="ef6f6-128">設定使用 wcf-custom 配接器和 SQL 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="ef6f6-128">Configure a port using the WCF-custom adapter and SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-custom-adapter-and-sql-adapter.md)  
  
-   [<span data-ttu-id="ef6f6-129">設定使用 WCF-SQL 配接器的連接埠</span><span class="sxs-lookup"><span data-stu-id="ef6f6-129">Configure a port using the WCF-SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/configure-a-port-using-the-wcf-sql-adapter.md)  
  
## <a name="see-also"></a><span data-ttu-id="ef6f6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef6f6-130">See Also</span></span>  
[<span data-ttu-id="ef6f6-131">開發 BizTalk 應用程式與 SQL 配接器的建置組塊</span><span class="sxs-lookup"><span data-stu-id="ef6f6-131">Building blocks to develop BizTalk applications with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md)