---
title: "使用 TIBCO EMS 訊息內容屬性 |Microsoft 文件"
description: "使用 BizTalk Server 協調流程中的 TIBCO Enterprise Message System 訊息描述元欄位"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 163ac2cf-0e2d-4780-b398-baa825f92b00
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5433e454d161c77ac140167e9af082eaee7c2032
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="message-context-properties-in-tibco-ems"></a><span data-ttu-id="cf52c-103">在 TIBCO EMS 的訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="cf52c-103">Message Context Properties in TIBCO EMS</span></span>

## <a name="tibcoemspropertiesdll"></a><span data-ttu-id="cf52c-104">TibcoEMSProperties.dll</span><span class="sxs-lookup"><span data-stu-id="cf52c-104">TibcoEMSProperties.dll</span></span>
<span data-ttu-id="cf52c-105">若要從 BizTalk Server 協調流程存取 TIBCO Enterprise Message System 訊息描述元欄位，您必須加入參考**Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll**至您的專案。</span><span class="sxs-lookup"><span data-stu-id="cf52c-105">To access TIBCO Enterprise Message System message descriptor fields from a BizTalk Server orchestration, you must add a reference to **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** to your project.</span></span> <span data-ttu-id="cf52c-106">這個組件位於 **\<TIBCO EMS_Adapter_installation_directory\>\bin**。</span><span class="sxs-lookup"><span data-stu-id="cf52c-106">This assembly is located in **\<TIBCO EMS_Adapter_installation_directory\>\bin**.</span></span> <span data-ttu-id="cf52c-107">在參考這個屬性結構描述之後，各種 BizTalk Server 開發工具 (例如協調流程設計師裡的訊息指派圖形) 就可以存取其他內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cf52c-107">After you reference this TIBCO EMS property schema, additional context properties can be accessed by various BizTalk Server development tools (for example, the message assignment shape in the orchestration designer).</span></span>  
  
## <a name="access-context-properties"></a><span data-ttu-id="cf52c-108">存取內容屬性</span><span class="sxs-lookup"><span data-stu-id="cf52c-108">Access context Properties</span></span>  
 <span data-ttu-id="cf52c-109">若要存取內容屬性，您必須指定在 TIBCO EMS 命名空間內的其中一個可用內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cf52c-109">To access a context property, you specify one of the available context properties in the TIBCO EMS namespace.</span></span> <span data-ttu-id="cf52c-110">若要讀取從繫結至 BizTalk Adapter for TIBCO EMS 之連接埠所接收訊息的內容屬性，請在運算式中使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="cf52c-110">To read the context property of a message received from a port bound to BizTalk Adapter for TIBCO EMS, use the following syntax in an expression:</span></span>  
  
```  
Message(TibcoEMS.Property)  
```  
  
 <span data-ttu-id="cf52c-111">如需詳細資訊，請參閱[TIBCO 企業訊息服務訊息描述元屬性](../core/tibco-enterprise-message-service-message-descriptor-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="cf52c-111">For more information, see [TIBCO Enterprise Message Service Message Descriptor Properties](../core/tibco-enterprise-message-service-message-descriptor-properties.md).</span></span>  
  
 <span data-ttu-id="cf52c-112">在 BizTalk Server 中，訊息都是永遠不變的。</span><span class="sxs-lookup"><span data-stu-id="cf52c-112">In BizTalk Server, messages are immutable.</span></span> <span data-ttu-id="cf52c-113">因此，若要指派訊息內容屬性值，請建立新訊息，設定訊息內容 (可能是透過指派現有訊息的方式)，然後再設定您需要的屬性。</span><span class="sxs-lookup"><span data-stu-id="cf52c-113">Therefore, to assign a message context property value, you create a new message, set the message content (possibly by assigning an existing message), and then set the properties that you need.</span></span>  
  
 <span data-ttu-id="cf52c-114">若要將 TIBCO EMS 內容屬性指派給訊息，而該訊息的目標是繫結到 BizTalk Adapter for TIBCO EMS 的傳送埠，請使用訊息指派運算子，並指定 TIBCO EMS 運算空間中其中一個可用的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="cf52c-114">To assign TIBCO EMS context properties to a message destined to a send port that is bound to BizTalk Adapter for TIBCO EMS, use the message assignment operator and specify one of the available context properties in the TIBCO EMS namespace.</span></span> <span data-ttu-id="cf52c-115">其語法如下：</span><span class="sxs-lookup"><span data-stu-id="cf52c-115">The syntax is as follows:</span></span>  
  
```  
Message(TibcoEMS.Property) = value;  
```  
  
## <a name="next-steps"></a><span data-ttu-id="cf52c-116">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="cf52c-116">Next steps</span></span>
-   [<span data-ttu-id="cf52c-117">TIBCO EMS 訊息描述元屬性與值</span><span class="sxs-lookup"><span data-stu-id="cf52c-117">TIBCO EMS Message Descriptor properties & values</span></span>](../core/tibco-enterprise-message-service-message-descriptor-properties.md)  
  
-   [<span data-ttu-id="cf52c-118">教學課程：使用訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="cf52c-118">Tutorial: Use Message Context Properties</span></span>](../core/tutorial-using-message-context-properties.md)