---
title: "設定識別項 (AS2) |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 29f12696-8257-4664-8e61-292678e98b6b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac5f85187a49f3ab5248f12aceba74731ed7e915
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-identifiers-as2"></a><span data-ttu-id="9c634-102">設定識別項 (AS2)</span><span class="sxs-lookup"><span data-stu-id="9c634-102">Configuring Identifiers (AS2)</span></span>
<span data-ttu-id="9c634-103">在夥伴協議中，您必須指定傳送者與接收者合作對象。</span><span class="sxs-lookup"><span data-stu-id="9c634-103">In the partner agreement, you must specify the sender and receiver parties.</span></span> <span data-ttu-id="9c634-104">這些值也會用來解析輸入或輸出訊息的協議。</span><span class="sxs-lookup"><span data-stu-id="9c634-104">These values are also used for agreement resolution for the inbound or outbound messages.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c634-105">下列屬性會停用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="9c634-105">The following properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  -   <span data-ttu-id="9c634-106">**AS2To**下**其他協議解析程式**> 一節。</span><span class="sxs-lookup"><span data-stu-id="9c634-106">**AS2To** under **Additional Agreement Resolvers** section.</span></span>  
>   
>  <span data-ttu-id="9c634-107">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="9c634-107">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="9c634-108">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c634-108">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9c634-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="9c634-109">Prerequisites</span></span>  
 <span data-ttu-id="9c634-110">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="9c634-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-identifier-properties"></a><span data-ttu-id="9c634-111">設定識別項屬性</span><span class="sxs-lookup"><span data-stu-id="9c634-111">To configure the identifier properties</span></span>  
  
1.  <span data-ttu-id="9c634-112">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="9c634-112">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="9c634-113">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="9c634-113">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9c634-114">在單向協議索引標籤上，按一下 **識別碼**。</span><span class="sxs-lookup"><span data-stu-id="9c634-114">On a one-way agreement tab, click **Identifiers**.</span></span>  
  
3.  <span data-ttu-id="9c634-115">在**AS2-從**頁面上，指定傳送 AS2 訊息的交易夥伴的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c634-115">In the **AS2-From** page, specify the name of the trading partner sending the AS2 message.</span></span>  
  
4.  <span data-ttu-id="9c634-116">在**AS2-要**頁面上，指定交易夥伴接收 AS2 訊息的名稱。</span><span class="sxs-lookup"><span data-stu-id="9c634-116">In the **AS2-To** page, specify the name of the trading partner receiving the AS2 message.</span></span>  
  
5.  <span data-ttu-id="9c634-117">在下**其他協議解析程式** 區段中，針對**AS2To**屬性，接收訊息的夥伴輸入其他別名。</span><span class="sxs-lookup"><span data-stu-id="9c634-117">Under the **Additional Agreement Resolvers** section, for the **AS2To** property, enter an additional alias for the partner that receives the message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9c634-118">此屬性是選擇項。</span><span class="sxs-lookup"><span data-stu-id="9c634-118">This property is optional.</span></span> <span data-ttu-id="9c634-119">此屬性適用於回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="9c634-119">This property is available for backward compatibility.</span></span> <span data-ttu-id="9c634-120">將合作對象定義從 BizTalk Server 2006 R2 或 BizTalk Server 2009 移轉至 [!INCLUDE[prague](../includes/prague-md.md)] 時，會將舊版 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的合作對象名稱做為此屬性的值納入。</span><span class="sxs-lookup"><span data-stu-id="9c634-120">When a party definition is migrated from BizTalk Server 2006 R2 or BizTalk Server 2009 to [!INCLUDE[prague](../includes/prague-md.md)], the name of the party in the previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is included as a value for this property.</span></span> <span data-ttu-id="9c634-121">這樣可確保會進行協議解析，而且現有的應用程式與夥伴定義可與 [!INCLUDE[prague](../includes/prague-md.md)] 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="9c634-121">This ensures that the agreement resolution happens and the existing applications and partner definitions can be used with [!INCLUDE[prague](../includes/prague-md.md)].</span></span>  
  
6.  <span data-ttu-id="9c634-122">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9c634-122">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c634-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c634-123">See Also</span></span>  
 [<span data-ttu-id="9c634-124">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="9c634-124">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)