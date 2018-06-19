---
title: 設定動態傳送埠以傳送 EDI 交換和通知 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a124059c-c29c-4a7f-a8a3-13dffc09ae5c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a793fc22394c2b4d294bcd48fae1f9403ae9278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232814"
---
# <a name="configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments"></a><span data-ttu-id="83eb9-102">將動態傳送埠設定為傳送 EDI 交換和通知</span><span class="sxs-lookup"><span data-stu-id="83eb9-102">Configuring a Dynamic Send Port to Send EDI Interchanges and Acknowledgments</span></span>
<span data-ttu-id="83eb9-103">若要傳送 EDI 交換或通知，您可以使用靜態傳送埠或動態傳送埠。</span><span class="sxs-lookup"><span data-stu-id="83eb9-103">To send an EDI acknowledgment or interchange, you can use either a static send port or a dynamic send port.</span></span> <span data-ttu-id="83eb9-104">動態傳送埠可讓您交換傳送至多個目的地，其中，因為它以解析協議，並決定目的地址根據 DestinationPartyName 內容屬性中的值。</span><span class="sxs-lookup"><span data-stu-id="83eb9-104">A dynamic send port enables you to send an interchange to any one of multiple destinations, because it resolves the agreement and determines the destination address based upon the value in the DestinationPartyName context property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83eb9-105">如果您要傳送 EDI 交換接收，XML 訊息為基礎，而且您使用通過接收管線接收該應用程式，您就必須升級 DestinationPartyName 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="83eb9-105">If you are sending an EDI interchange that is based upon an XML message received, and you are using a passthrough receive pipeline to receive that application, you will have to promote the DestinationPartyName context property.</span></span> <span data-ttu-id="83eb9-106">如需詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="83eb9-106">For more information, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83eb9-107">如果動態傳送埠會傳送通知，表示 DestinationPartyName 內容屬性已經升級，因為接收交換之連接埠中的 EDI 解譯器會填入通知上的 DestinationPartyName 屬性。</span><span class="sxs-lookup"><span data-stu-id="83eb9-107">If the dynamic send port will be sending an acknowledgment, the DestinationPartyName context property will already be promoted because the EDI Disassembler in the port that received the interchange populates the DestinationPartyName property on the acknowledgment.</span></span>  
  
 <span data-ttu-id="83eb9-108">若要建立單向動態傳送埠，請使用下列組態：</span><span class="sxs-lookup"><span data-stu-id="83eb9-108">To create a one-way dynamic send port, use the following configuration:</span></span>  
  
|<span data-ttu-id="83eb9-109">位置</span><span class="sxs-lookup"><span data-stu-id="83eb9-109">Location</span></span>|<span data-ttu-id="83eb9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="83eb9-110">Property</span></span>|<span data-ttu-id="83eb9-111">設定</span><span class="sxs-lookup"><span data-stu-id="83eb9-111">Setting</span></span>|  
|--------------|--------------|-------------|  
|<span data-ttu-id="83eb9-112">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="83eb9-112">**Send Port Properties: General**</span></span>|<span data-ttu-id="83eb9-113">連接埠類型</span><span class="sxs-lookup"><span data-stu-id="83eb9-113">Port type</span></span>|<span data-ttu-id="83eb9-114">動態單向</span><span class="sxs-lookup"><span data-stu-id="83eb9-114">Dynamic One-Way</span></span>|  
|<span data-ttu-id="83eb9-115">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="83eb9-115">**Send Port Properties: General**</span></span>|<span data-ttu-id="83eb9-116">傳送處理常式</span><span class="sxs-lookup"><span data-stu-id="83eb9-116">Send handler</span></span>|<span data-ttu-id="83eb9-117">BizTalkServerApplication</span><span class="sxs-lookup"><span data-stu-id="83eb9-117">BizTalkServerApplication</span></span>|  
|<span data-ttu-id="83eb9-118">**傳送埠屬性： 一般**</span><span class="sxs-lookup"><span data-stu-id="83eb9-118">**Send Port Properties: General**</span></span>|<span data-ttu-id="83eb9-119">傳送管線</span><span class="sxs-lookup"><span data-stu-id="83eb9-119">Send pipeline</span></span>|<span data-ttu-id="83eb9-120">EdiSend</span><span class="sxs-lookup"><span data-stu-id="83eb9-120">EdiSend</span></span>|  
|<span data-ttu-id="83eb9-121">**檔案傳輸屬性： 驗證**</span><span class="sxs-lookup"><span data-stu-id="83eb9-121">**FILE Transport Properties: Authentication**</span></span>|<span data-ttu-id="83eb9-122">當主控件沒有存取網路共用的權限時，即使用這些認證 (使用使用者名稱和密碼)</span><span class="sxs-lookup"><span data-stu-id="83eb9-122">Use these credentials when host does not have access to network share (with User name and Password)</span></span>|<span data-ttu-id="83eb9-123">如果需要驗證則予以設定。</span><span class="sxs-lookup"><span data-stu-id="83eb9-123">Set if authentication is required.</span></span>|  
|<span data-ttu-id="83eb9-124">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="83eb9-124">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="83eb9-125">屬性</span><span class="sxs-lookup"><span data-stu-id="83eb9-125">Property</span></span>|<span data-ttu-id="83eb9-126">BTS.MessageType</span><span class="sxs-lookup"><span data-stu-id="83eb9-126">BTS.MessageType</span></span>|  
|<span data-ttu-id="83eb9-127">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="83eb9-127">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="83eb9-128">運算子</span><span class="sxs-lookup"><span data-stu-id="83eb9-128">Operator</span></span>|==|  
|<span data-ttu-id="83eb9-129">**傳送埠屬性： 篩選**</span><span class="sxs-lookup"><span data-stu-id="83eb9-129">**Send Port Properties: Filters**</span></span>|<span data-ttu-id="83eb9-130">值</span><span class="sxs-lookup"><span data-stu-id="83eb9-130">Value</span></span>|<span data-ttu-id="83eb9-131">**交換**:</span><span class="sxs-lookup"><span data-stu-id="83eb9-131">**For interchanges**:</span></span><br /><br /> <span data-ttu-id="83eb9-132">- `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`或</span><span class="sxs-lookup"><span data-stu-id="83eb9-132">- `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, or</span></span><br /><br /> <span data-ttu-id="83eb9-133">-                   `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`或</span><span class="sxs-lookup"><span data-stu-id="83eb9-133">-                   `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`,or</span></span><br /><br /> <span data-ttu-id="83eb9-134">**針對通知**:</span><span class="sxs-lookup"><span data-stu-id="83eb9-134">**For ACKs**:</span></span><br /><br /> <span data-ttu-id="83eb9-135">-                   `http://schemas.microsoft.com/Edi/X12#X12_997_Root`或</span><span class="sxs-lookup"><span data-stu-id="83eb9-135">-                   `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, or</span></span><br /><br /> <span data-ttu-id="83eb9-136">-                   `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`或</span><span class="sxs-lookup"><span data-stu-id="83eb9-136">-                   `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, or</span></span><br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="setting-agreement-properties"></a><span data-ttu-id="83eb9-137">設定協議屬性</span><span class="sxs-lookup"><span data-stu-id="83eb9-137">Setting Agreement Properties</span></span>  
 <span data-ttu-id="83eb9-138">建立傳送埠之後，您需要設定所需的函式的傳送管線的協議屬性。</span><span class="sxs-lookup"><span data-stu-id="83eb9-138">After creating the send port, you need to set the agreement properties required for the send pipeline to function.</span></span> <span data-ttu-id="83eb9-139">這些屬性會設定各種頁面中**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="83eb9-139">These properties are set in various pages of the **Agreement Properties** dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83eb9-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83eb9-140">See Also</span></span>  
 [<span data-ttu-id="83eb9-141">設定 EDI 解決方案的連接埠</span><span class="sxs-lookup"><span data-stu-id="83eb9-141">Configuring Ports for an EDI Solution</span></span>](../core/configuring-ports-for-an-edi-solution.md)