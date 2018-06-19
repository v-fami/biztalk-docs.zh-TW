---
title: 設定後援通知屬性 (X12) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce33f5dd-fbd5-448c-8ea3-05dd1467131a
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 216961dea0bdf4a67c550fba8a599eff2d0c89ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232830"
---
# <a name="configuring-fallback-acknowledgement-properties-x12"></a><span data-ttu-id="39847-102">設定後援通知屬性 (X12)</span><span class="sxs-lookup"><span data-stu-id="39847-102">Configuring Fallback Acknowledgement Properties (X12)</span></span>
<span data-ttu-id="39847-103">在後援協議中，您可以指定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在收到來自合作對象的 X12 編碼交換後，應如何產生通知，以及應對合作對象傳回哪種類型的通知。</span><span class="sxs-lookup"><span data-stu-id="39847-103">In the fallback agreement, you can specify how [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generates acknowledgments in response to X12-encoded interchanges received from the party and what type of acknowledgment to return to a party.</span></span> <span data-ttu-id="39847-104">本節提供如何進行相同設定的指示。</span><span class="sxs-lookup"><span data-stu-id="39847-104">This section provides instructions on how to do the same.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39847-105">此處所說明的通知屬性也適用於 HIPAA 通知。</span><span class="sxs-lookup"><span data-stu-id="39847-105">The acknowledgement properties described here apply also for HIPAA acknowledgements.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="39847-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="39847-106">Prerequisites</span></span>  
 <span data-ttu-id="39847-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="39847-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-x12-ack-properties"></a><span data-ttu-id="39847-108">若要設定 X12 通知屬性</span><span class="sxs-lookup"><span data-stu-id="39847-108">To configure X12 ACK properties</span></span>  
  
1.  <span data-ttu-id="39847-109">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="39847-109">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **X12 Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="39847-110">在**X12 後援設定**對話方塊中，於**X12 協議頁面**索引標籤，下方**交換設定**區段中，按一下**通知**.</span><span class="sxs-lookup"><span data-stu-id="39847-110">In the **X12 Fallback Settings** dialog box, in the **X12 Agreement Pages** tab, under the **Interchange Settings** section, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="39847-111">選取**預期 TA1**技術 (TA1) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="39847-111">Select **TA1 Expected** to return a technical (TA1) acknowledgment to the interchange sender.</span></span>  
  
4.  <span data-ttu-id="39847-112">選取**預期 997**功能 (997) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="39847-112">Select **997 Expected** to return a functional (997) acknowledgment to the interchange sender.</span></span>  
  
5.  <span data-ttu-id="39847-113">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="39847-113">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39847-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39847-114">See Also</span></span>  
 [<span data-ttu-id="39847-115">設定 X12 後援協議屬性的交換處理</span><span class="sxs-lookup"><span data-stu-id="39847-115">Configuring X12 Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-x12-fallback-agreement-properties-for-interchange-processing.md)