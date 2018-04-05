---
title: 設定 AS2 管線屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edir2.AS2.pipeline.properties
ms.assetid: 7faf6b05-710a-4d00-8c77-590ce9d9f962
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e41afd99e7af1441e2d3d8cc936c04cd9321779
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-as2-pipeline-properties"></a><span data-ttu-id="63325-102">設定 AS2 管線屬性</span><span class="sxs-lookup"><span data-stu-id="63325-102">Configuring AS2 Pipeline Properties</span></span>
<span data-ttu-id="63325-103">管線屬性可在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷會解析為所傳送或所接收交換的協議時，用來處理內送或外寄 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="63325-103">Pipeline properties are used in processing an incoming or outgoing AS2 message when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] has not been able to determine the agreement that resolves to the sent or received interchange.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63325-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="63325-104">Prerequisites</span></span>  
 <span data-ttu-id="63325-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="63325-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="as2-pipeline-properties"></a><span data-ttu-id="63325-106">AS2 管線屬性</span><span class="sxs-lookup"><span data-stu-id="63325-106">AS2 Pipeline Properties</span></span>  
 <span data-ttu-id="63325-107">您可以在 AS2 管線中設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="63325-107">The following property can be set in AS2 pipelines:</span></span>  
  
|<span data-ttu-id="63325-108">屬性</span><span class="sxs-lookup"><span data-stu-id="63325-108">Property</span></span>|<span data-ttu-id="63325-109">使用</span><span class="sxs-lookup"><span data-stu-id="63325-109">Use</span></span>|<span data-ttu-id="63325-110">值</span><span class="sxs-lookup"><span data-stu-id="63325-110">Values</span></span>|<span data-ttu-id="63325-111">管線/階段</span><span class="sxs-lookup"><span data-stu-id="63325-111">Pipeline/Stage</span></span>|  
|--------------|---------|------------|---------------------|  
|<span data-ttu-id="63325-112">ContentTransferEncoding</span><span class="sxs-lookup"><span data-stu-id="63325-112">ContentTransferEncoding</span></span>|<span data-ttu-id="63325-113">指出將使用哪個方法，以 ASCII 文字格式表示二進位資料。</span><span class="sxs-lookup"><span data-stu-id="63325-113">Indicates which method will be used for representing binary data in ASCII text format.</span></span>|<span data-ttu-id="63325-114">8bit (預設值)</span><span class="sxs-lookup"><span data-stu-id="63325-114">8bit (default)</span></span><br /><br /> <span data-ttu-id="63325-115">7bit</span><span class="sxs-lookup"><span data-stu-id="63325-115">7bit</span></span><br /><br /> <span data-ttu-id="63325-116">8bit</span><span class="sxs-lookup"><span data-stu-id="63325-116">8bit</span></span>|<span data-ttu-id="63325-117">AS2EdiSend/編碼</span><span class="sxs-lookup"><span data-stu-id="63325-117">AS2EdiSend/Encode</span></span><br /><br /> <span data-ttu-id="63325-118">AS2Send/編碼</span><span class="sxs-lookup"><span data-stu-id="63325-118">AS2Send/Encode</span></span>|  
  
### <a name="to-set-a-pipeline-property"></a><span data-ttu-id="63325-119">若要設定管線屬性</span><span class="sxs-lookup"><span data-stu-id="63325-119">To set a pipeline property</span></span>  
  
1.  <span data-ttu-id="63325-120">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中，以滑鼠右鍵按一下使用您要設定屬性之管線的接收位置或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="63325-120">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the receive location or send port using the pipeline that you want to set properties for.</span></span> <span data-ttu-id="63325-121">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="63325-121">Click **Properties**.</span></span>  
  
2.  <span data-ttu-id="63325-122">按一下要設定屬性之管線旁邊的省略符號按鈕 (?。</span><span class="sxs-lookup"><span data-stu-id="63325-122">Click the ellipsis button (…) next to the pipeline that you want to set properties for.</span></span>  
  
3.  <span data-ttu-id="63325-123">輸入值的屬性，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="63325-123">Enter the value for the property, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63325-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63325-124">See Also</span></span>  
 [<span data-ttu-id="63325-125">開發和設定 BizTalk Server AS2 解決方案</span><span class="sxs-lookup"><span data-stu-id="63325-125">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)