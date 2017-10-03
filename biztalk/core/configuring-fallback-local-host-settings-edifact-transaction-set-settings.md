---
title: "設定後援本機主機設定 （EDIFACT 交易集設定） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0142b3fc-009f-4da5-b34d-dddf4fb96e0f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 931db62edda264a6fff0ddb422bd41b243cd29ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-fallback-local-host-settings-edifact-transaction-set-settings"></a><span data-ttu-id="c7d1a-102">設定後援本機主機設定 (EDIFACT 交易集設定)</span><span class="sxs-lookup"><span data-stu-id="c7d1a-102">Configuring Fallback Local Host Settings (EDIFACT-Transaction Set Settings)</span></span>
<span data-ttu-id="c7d1a-103">為了處理內送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 必須要判斷它需要用來處理和驗證該交換的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-103">To process an incoming interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] must determine the schema that it needs to use in processing and validating the interchange.</span></span> <span data-ttu-id="c7d1a-104">這個過程包括判斷與該結構描述相關聯的目標命名空間，以及判斷要使用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-104">This consists of determining the target namespace associated with the schema, and determining the schema to be used.</span></span> <span data-ttu-id="c7d1a-105">您要在這頁後援協議中，輸入要用來判斷上述目標命名空間的屬性。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-105">In this page of fallback agreement, you enter the properties to be used in determining the target namespace.</span></span> <span data-ttu-id="c7d1a-106">BizTalk Server 如何判斷結構描述中描述[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-106">How BizTalk Server determines the schema is described in [Agreement Resolution, Schema Discovery, and Authorization for Received EDI Messages](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c7d1a-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="c7d1a-107">Prerequisites</span></span>  
 <span data-ttu-id="c7d1a-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-local-host-settings-for-transaction-sets"></a><span data-ttu-id="c7d1a-109">若要設定交易集的本機主機設定</span><span class="sxs-lookup"><span data-stu-id="c7d1a-109">To configure local host settings for transaction sets</span></span>  
  
1.  <span data-ttu-id="c7d1a-110">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-110">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Parties** node, and then click **EDIFACT Fallback Settings**.</span></span>  
  
2.  <span data-ttu-id="c7d1a-111">在**EDIFACT 後援設定**對話方塊中，於**EDIFACT 協議頁面**索引標籤，下方**交易集設定**區段中，按一下**本機主機設定**。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-111">In the **EDIFACT Fallback Settings** dialog box, in the **EDIFACT Agreement Pages** tab, under the **Transaction Set Settings** section, click **Local Host Settings**.</span></span>  
  
3.  <span data-ttu-id="c7d1a-112">選取**建立針對尾端分隔符號的空 XML 標記**將交換傳送者包含尾端分隔符號的空 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-112">Select **Create empty XML tags for trailing separators** to have the interchange sender include empty XML tags for trailing separators.</span></span>  
  
4.  <span data-ttu-id="c7d1a-113">選取**使用點 （.） 做為小數分隔符號**BizTalk Server 以啟用含小數的交換建立 XML 訊息中包含點 （.）。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-113">Select **Use Dot (.) as decimal separator** to enable BizTalk Server include a dot (.) in the XML message created out of an interchange that contains a decimal number.</span></span>  
  
5.  <span data-ttu-id="c7d1a-114">如**目標命名空間**、 輸入 （或從下拉式清單中選取） 目標命名空間的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會使用來決定處理所接收的訊息之結構描述</span><span class="sxs-lookup"><span data-stu-id="c7d1a-114">For **Target Namespace**, enter (or select from the drop-down list) the target namespace that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to determine the schema to process the received message with</span></span>  
  
6.  <span data-ttu-id="c7d1a-115">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c7d1a-115">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d1a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7d1a-116">See Also</span></span>  
 [<span data-ttu-id="c7d1a-117">EDIFACT 後援協議屬性設定為交易集設定</span><span class="sxs-lookup"><span data-stu-id="c7d1a-117">Configuring EDIFACT Fallback Agreement Properties for Transaction Set Settings</span></span>](../core/configuring-edifact-fallback-agreement-properties-for-transaction-set-settings.md)