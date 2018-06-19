---
title: 設定後援通知屬性 (EDIFACT) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6062b881-3214-4e68-acbc-1f8c255fd86b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d9369eb7fff1a6217da774aaf62af6e036d0abd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233014"
---
# <a name="configuring-fallback-acknowledgement-properties-edifact"></a><span data-ttu-id="63eda-102">設定後援通知屬性 (EDIFACT)</span><span class="sxs-lookup"><span data-stu-id="63eda-102">Configuring Fallback Acknowledgement Properties (EDIFACT)</span></span>
<span data-ttu-id="63eda-103">在後援協議中，您可以指定要傳回給合作對象的通知類型。</span><span class="sxs-lookup"><span data-stu-id="63eda-103">In the fallback agreement, you can specify what type of acknowledgment to return to a party.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="63eda-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="63eda-104">Prerequisites</span></span>  
 <span data-ttu-id="63eda-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="63eda-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-edifact-ack-contrl-properties"></a><span data-ttu-id="63eda-106">若要設定 EDIFACT 通知 (CONTRL) 屬性</span><span class="sxs-lookup"><span data-stu-id="63eda-106">To configure EDIFACT ACK (CONTRL) properties</span></span>  
  
1.  <span data-ttu-id="63eda-107">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="63eda-107">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="63eda-108">在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交換設定**區段中，按一下**通知**。</span><span class="sxs-lookup"><span data-stu-id="63eda-108">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Interchange Settings** section, click **Acknowledgements**.</span></span>  
  
3.  <span data-ttu-id="63eda-109">選取**訊息回條 (CONTRL 必須是)** 技術 (CONTRL) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="63eda-109">Select **Receipt of message (CONTRL) expected** to return a technical (CONTRL) acknowledgment to the interchange sender.</span></span>  
  
4.  <span data-ttu-id="63eda-110">選取**通知 (CONTRL) 必須是**功能 (CONTRL) 通知傳回給交換傳送者。</span><span class="sxs-lookup"><span data-stu-id="63eda-110">Select **Acknowledgement (CONTRL) expected** to return a functional (CONTRL) acknowledgment to the interchange sender.</span></span>  
  
5.  <span data-ttu-id="63eda-111">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="63eda-111">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63eda-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63eda-112">See Also</span></span>  
 [<span data-ttu-id="63eda-113">設定 EDIFACT 後援協議屬性的交換處理</span><span class="sxs-lookup"><span data-stu-id="63eda-113">Configuring EDIFACT Fallback Agreement Properties for Interchange Processing</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-interchange-processing.md)