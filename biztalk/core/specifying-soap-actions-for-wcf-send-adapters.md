---
title: 指定的 SOAP 動作，wcf 傳送配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send adapters, mapping
- send adapters, WCF services
- mapping, send adapters
- mapping, WCF send adapters
ms.assetid: fa9878eb-65b5-4ccc-b727-ff7e09ba6302
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47781b2b8add675207136248b38b0dadfe6b5610
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023492"
---
# <a name="specifying-soap-actions-for-wcf-send-adapters"></a><span data-ttu-id="24efb-102">指定 WCF 傳送配接器的 SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="24efb-102">Specifying SOAP Actions for WCF Send Adapters</span></span>
<span data-ttu-id="24efb-103">您可以設定**WCF。動作**內容 WCF 傳送配接器傳輸屬性對話方塊中，或在協調流程中的屬性**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="24efb-103">You can set the **WCF.Action** context property in the WCF send adapter transport properties dialog box or in the orchestration **Expression** shapes.</span></span> <span data-ttu-id="24efb-104">如果您將設定**WCF。動作**協調流程中的內容屬性，您必須保持**動作**[WCF 配接器傳輸屬性] 對話方塊中的靜態傳送埠中的空白欄位。</span><span class="sxs-lookup"><span data-stu-id="24efb-104">If you set the **WCF.Action** context property in the orchestration, you need to leave the **Action** field blank in the WCF adapter transport properties dialog box for the static send ports.</span></span> <span data-ttu-id="24efb-105">如果您也會在靜態傳送埠中，指定動作**WCF。動作**將會覆寫您在協調流程中設定的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="24efb-105">If you also specify an action in the static send ports, the **WCF.Action** context property you set in the orchestration will be overridden.</span></span>  
  
 <span data-ttu-id="24efb-106">此外，有兩種方式來指定此屬性： 單一動作格式和動作對應格式。</span><span class="sxs-lookup"><span data-stu-id="24efb-106">Moreover, there are two ways to specify this property: the single action format and the action mapping format.</span></span> <span data-ttu-id="24efb-107">如果您在單一動作格式中設定這個屬性 — 比方說， http://MyService/IMyContract/MyAction1— 在 WCF 中的 SOAP 動作傳送配接器傳輸屬性 對話方塊中，針對外寄訊息一律設為這個屬性中指定的值。</span><span class="sxs-lookup"><span data-stu-id="24efb-107">If you set this property in the single action format—for example, http://MyService/IMyContract/MyAction1—the SOAP action in the WCF send adapter transport properties dialog box for outgoing messages is always set to the value specified in this property.</span></span> <span data-ttu-id="24efb-108">或者，您可以設定於協調流程的單一動作格式**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="24efb-108">Alternatively, you can set the single action format in the orchestration **Expression** shape.</span></span> <span data-ttu-id="24efb-109">例如，</span><span class="sxs-lookup"><span data-stu-id="24efb-109">For example,</span></span>  
  
```  
OutboundMessage(WCF.Action)="http://MyService/IMyContract/MyAction1";  
```  
  
 <span data-ttu-id="24efb-110">如果您是以動作對應格式設定這個屬性外, 寄 SOAP 動作取決於**BTS。作業**內容屬性。</span><span class="sxs-lookup"><span data-stu-id="24efb-110">If you set this property in the action mapping format, the outgoing SOAP action is determined by the **BTS.Operation** context property.</span></span> <span data-ttu-id="24efb-111">比方說，如果此屬性設定為下列 XML 格式 wcf 傳送配接器傳輸屬性 對話方塊中， **BTS。作業**屬性設定為**Operation_1**在傳送埠協調流程中，WCF 傳送配接器會使用http://MyService/IMyContract/MyAction1外寄 SOAP 動作。</span><span class="sxs-lookup"><span data-stu-id="24efb-111">For example, if this property is set to the following XML format in the WCF send adapter transport properties dialog box and the **BTS.Operation** property is set to **Operation_1** in the send port in the orchestration, the WCF send adapter uses http://MyService/IMyContract/MyAction1 for the outgoing SOAP action.</span></span>  
  
```  
BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<Operation Name="Operation_1" Action="http://MyService/IMyContract/MyAction1" />  
<Operation Name="Operation_2" Action="http://MyService/IMyContract/MyAction2" />  
<Operation Name="Operation_3" Action="http://MyService/IMyContract/MyAction3" />  
</BtsActionMapping>  
```  
  
 <span data-ttu-id="24efb-112">指定動作對應**WCF。動作**中**運算式**圖形不支援。</span><span class="sxs-lookup"><span data-stu-id="24efb-112">Specifying action mapping for **WCF.Action** in an **Expression** shape is not supported.</span></span> <span data-ttu-id="24efb-113">您必須在 [WCF 傳輸屬性] 對話方塊中指定動作對應。</span><span class="sxs-lookup"><span data-stu-id="24efb-113">You need to specify the action mapping in the WCF transport properties dialog box.</span></span> <span data-ttu-id="24efb-114">WCF 配接器將會使用查詢的 SOAP 動作然後**BTS。作業**內容屬性，協調流程會設定為當傳送訊息的連接埠上作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="24efb-114">Then the WCF adapter will look up the SOAP action by using the **BTS.Operation** context property, which the orchestration sets to the name of the operation on the port where the message is sent.</span></span>  
  
 <span data-ttu-id="24efb-115">如果外寄訊息都會路由傳送以內容為基礎的路由 (CBR) 所在**http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation**屬性未設定，，WCF 傳送配接器會將整個動作對應字串設定為外寄 WCF 訊息的動作。</span><span class="sxs-lookup"><span data-stu-id="24efb-115">If outgoing messages are routed with content-based routing (CBR) where the **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** property is not set, WCF send adapters will set the whole action mapping string to the action of the outgoing WCF messages.</span></span> <span data-ttu-id="24efb-116">若要解決這個問題，您可以執行下列一種方法：</span><span class="sxs-lookup"><span data-stu-id="24efb-116">To work around this, you can do one of the following:</span></span>  
  
- <span data-ttu-id="24efb-117">設定傳送埠上的 [動作] 欄位http://MyService/IMyContract/MyAction1。</span><span class="sxs-lookup"><span data-stu-id="24efb-117">Set the action field on the send port to http://MyService/IMyContract/MyAction1.</span></span>  
  
- <span data-ttu-id="24efb-118">設定**BTS。作業**管線中的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="24efb-118">Set the **BTS.Operation** context property in a pipeline.</span></span> <span data-ttu-id="24efb-119">例如，設定的值**http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation**為 Operation1。</span><span class="sxs-lookup"><span data-stu-id="24efb-119">For example, set the value of **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** to Operation1.</span></span>  
  
- <span data-ttu-id="24efb-120">將動作欄位保留空白，並且改用內送訊息中的動作。</span><span class="sxs-lookup"><span data-stu-id="24efb-120">Leave the action field blank and use the action from the incoming message instead.</span></span>  
  
  <span data-ttu-id="24efb-121">您也可以使用 [BizTalk WCF 服務使用精靈]，來搭配使用 WCF 服務與單一動作或動作對應。</span><span class="sxs-lookup"><span data-stu-id="24efb-121">You can also use the BizTalk WCF Service Consuming Wizard to consume the WCF services with single action or action mapping.</span></span> <span data-ttu-id="24efb-122">如需詳細資訊，請參閱 <<c0> [ 如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)。</span><span class="sxs-lookup"><span data-stu-id="24efb-122">For more details, see [How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24efb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24efb-123">See Also</span></span>  
 [<span data-ttu-id="24efb-124">使用 WCF 配接器內容屬性設定動態傳送埠</span><span class="sxs-lookup"><span data-stu-id="24efb-124">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)