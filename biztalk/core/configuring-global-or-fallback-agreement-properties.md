---
title: "設定全域或後援協議屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c375d03-6f22-4a67-9eac-d8896de2f7ee
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0eb693a17cad17eadaf0d005d12075dde30daa33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-global-or-fallback-agreement-properties"></a><span data-ttu-id="2b21e-102">設定全域或後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="2b21e-102">Configuring Global or Fallback Agreement Properties</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="2b21e-103"> 找不到可解析交換的協議時，就會使用後援協議屬性來處理訊息。</span><span class="sxs-lookup"><span data-stu-id="2b21e-103"> uses fallback agreement properties to process a message when it does not discover an agreement to resolve to for an interchange.</span></span> <span data-ttu-id="2b21e-104">後援協議屬性不適用於已知道協議的情況，而且也不適用於任何或所有協議。</span><span class="sxs-lookup"><span data-stu-id="2b21e-104">Fallback agreement properties are not used when the agreement is known, and do not apply to any or all agreements.</span></span>  
  
 <span data-ttu-id="2b21e-105">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到訊息時，它會嘗試比對協議的傳送者資訊與訊息中的傳送者資訊。</span><span class="sxs-lookup"><span data-stu-id="2b21e-105">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a message, it attempts to match the sender information for an agreement with the sender information in the message.</span></span> <span data-ttu-id="2b21e-106">傳送者資訊位於 X12 訊息的 ISA5 和 ISA6 資料項目，以及 EDIFACT 的 UNB2.1 和 UNB 2.2 資料項目中。</span><span class="sxs-lookup"><span data-stu-id="2b21e-106">The sender information is in the ISA5 and ISA6 data elements for X12 message, and the UNB2.1 and UNB 2.2 data elements for EDIFACT.</span></span> <span data-ttu-id="2b21e-107">協議資訊位於識別項中的索引標籤的單向協議索引標籤**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="2b21e-107">The agreement information is in the Identifier tabs in the one-way agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="2b21e-108">如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 找不到協議，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就會使用後援協議屬性來決定命名空間、處理訊息以及傳送任何通知。</span><span class="sxs-lookup"><span data-stu-id="2b21e-108">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not discover the agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback agreement properties to determine the namespace, process the message, and send any acknowledgments.</span></span>  
  
 <span data-ttu-id="2b21e-109">當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送訊息時，EDI 傳送管線會透過比對訂閱 MessageBox 中 XML 訊息的傳送埠，以及與協議關聯的傳送埠，來判斷訊息解析目標的協議。</span><span class="sxs-lookup"><span data-stu-id="2b21e-109">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends a message, the EDI send pipeline determines the agreement that the message resolves to by matching the send port that subscribes to the XML message in the MessageBox, with the send port associated with the agreement.</span></span> <span data-ttu-id="2b21e-110">如果傳送埠未與任何協議關聯，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 就會使用後援協議屬性來處理訊息以進行傳送。</span><span class="sxs-lookup"><span data-stu-id="2b21e-110">If the send port is not associated with an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the fallback agreement properties to process the message for sending.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b21e-111">傳送埠關聯只是執行協議解析的其中一種方式。</span><span class="sxs-lookup"><span data-stu-id="2b21e-111">Send port association is only one way of doing agreement resolution.</span></span> <span data-ttu-id="2b21e-112">如需外寄訊息的協議解析的詳細資訊，請參閱[協議解析和外寄 EDI 訊息的結構描述判斷](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="2b21e-112">For more information about agreement resolution for outgoing messages, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2b21e-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="2b21e-113">In This Section</span></span>  
  
-   [<span data-ttu-id="2b21e-114">設定 X12 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="2b21e-114">Configuring X12 Fallback Agreement Properties</span></span>](../core/configuring-x12-fallback-agreement-properties.md)  
  
-   [<span data-ttu-id="2b21e-115">設定 EDIFACT 後援協議屬性</span><span class="sxs-lookup"><span data-stu-id="2b21e-115">Configuring EDIFACT Fallback Agreement Properties</span></span>](../core/configuring-edifact-fallback-agreement-properties.md)  
  
## <a name="see-also"></a><span data-ttu-id="2b21e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b21e-116">See Also</span></span>  
 [<span data-ttu-id="2b21e-117">中協議 EDI 處理的角色</span><span class="sxs-lookup"><span data-stu-id="2b21e-117">The Role of Agreements in EDI Processing</span></span>](../core/the-role-of-agreements-in-edi-processing.md)