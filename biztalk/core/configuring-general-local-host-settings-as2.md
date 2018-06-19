---
title: 設定一般本機主機設定 (AS2) |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 980daac2-8387-44cc-ae55-38639f759668
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de5e5c076e6b245e4a662f8132d027e927df6142
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233814"
---
# <a name="configuring-general-local-host-settings-as2"></a><span data-ttu-id="0e395-102">設定一般本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="0e395-102">Configuring General Local Host Settings (AS2)</span></span>
<span data-ttu-id="0e395-103">在本機主機一般設定中，您可以指定 AS2 訊息的內容類型，以及是否保留檔案名稱做為 AS2 訊息標頭的一部分。</span><span class="sxs-lookup"><span data-stu-id="0e395-103">As part of the local host general settings, you can specify the content type of the AS2 messages and whether the file name is preserved as part of the AS2 message header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0e395-104">所有屬性會停都用此頁面上清除**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**時建立您要為其建立的合作對象 核取方塊協議。</span><span class="sxs-lookup"><span data-stu-id="0e395-104">All the properties are disabled on this page if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box while creating the party for which you are creating the agreement.</span></span>  
>   
>  <span data-ttu-id="0e395-105">只有在對應於合作對象送出交換屬性的單向協議索引標籤上，這些屬性才會變成停用狀態。</span><span class="sxs-lookup"><span data-stu-id="0e395-105">The properties are disabled only on the one-way agreement tab that corresponds to the properties for interchanges being sent from the party.</span></span> <span data-ttu-id="0e395-106">例如，如果您建立兩個合作對象的合作對象 A 與 Party B，並為合作對象 A 清除核取方塊，上述屬性清單會停用上**合作對象 a-> 合作對象 B**單向協議索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0e395-106">For example, if you create two parties Party A and Party B and for Party A, you cleared the check box, the above list of properties are disabled on the **Party A->Party B** one-way agreement tab.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0e395-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="0e395-107">Prerequisites</span></span>  
 <span data-ttu-id="0e395-108">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="0e395-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-the-general-settings"></a><span data-ttu-id="0e395-109">若要設定一般設定</span><span class="sxs-lookup"><span data-stu-id="0e395-109">To configure the general settings</span></span>  
  
1.  <span data-ttu-id="0e395-110">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="0e395-110">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="0e395-111">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0e395-111">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="0e395-112">在單向協議索引標籤底下**本機主機設定**區段中，按一下**一般**。</span><span class="sxs-lookup"><span data-stu-id="0e395-112">On a one-way agreement tab, under **Local Host Settings** section, click **General**.</span></span>  
  
3.  <span data-ttu-id="0e395-113">選取**傳送訊息之前檢查憑證撤銷清單**核取方塊，以判斷要用於簽署外寄訊息的憑證是否已包含在憑證撤銷清單中，表示它已被撤銷，或是否已經超過到期日。</span><span class="sxs-lookup"><span data-stu-id="0e395-113">Select the **Check Certification Revocation List before sending the message** check box to determine whether the certificate to be used in signing an outgoing messages has been included in the Certification Revocation List, indicating that it has been revoked, or whether the expiration date has passed.</span></span> <span data-ttu-id="0e395-114">如果是的話，BizTalk Server 便不會將訊息加密，但會擱置它。</span><span class="sxs-lookup"><span data-stu-id="0e395-114">If so, BizTalk Server will not encrypt the message, but will suspend it.</span></span> <span data-ttu-id="0e395-115">如果清除這個屬性，BizTalk Server 便不會執行這項檢查。</span><span class="sxs-lookup"><span data-stu-id="0e395-115">If this property is cleared, BizTalk Server will not perform this check.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e395-116">在擷取和搜尋憑證撤銷清單時會發生延遲。</span><span class="sxs-lookup"><span data-stu-id="0e395-116">There is a latency involved with retrieving and searching the certificate revocation list.</span></span>  
  
4.  <span data-ttu-id="0e395-117">如**預設內容類型**，選取合作對象必須用於外寄 AS2 訊息的預設內容類型。</span><span class="sxs-lookup"><span data-stu-id="0e395-117">For **Default content type**, select the default content type that the party must use for an outgoing AS2 message.</span></span> <span data-ttu-id="0e395-118">如果`ContentType`屬性設定的設定是用來產生外寄訊息，否則訊息內文部分內容中，這個值**預設內容類型**屬性使用。</span><span class="sxs-lookup"><span data-stu-id="0e395-118">If the `ContentType` property is set in the context for a message body part, that setting is used to generate the outgoing message; otherwise, the value of this **Default content type** property is used.</span></span>  
  
5.  <span data-ttu-id="0e395-119">選取**MIME 標頭中的傳輸檔案名稱**核取方塊做為輸出 AS2 訊息的 MIME 標頭的一部分傳送的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0e395-119">Select the **Transmit file name in MIME header** check box to send a file name as part of the MIME header for the outbound AS2 message.</span></span> <span data-ttu-id="0e395-120">若要指定檔案名稱，選取**指定檔案名稱**或**具有系統產生的檔案名稱**。</span><span class="sxs-lookup"><span data-stu-id="0e395-120">To specify the file name, select **Specify file name** or **Have system generate file name**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e395-121">選取**具有系統產生的檔案名稱**會產生新的 GUID 值做為 AS2 訊息中傳送的每個附件的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="0e395-121">Selecting **Have system generate file name** will generate a new GUID value as the file name of each attachment sent in the AS2 message.</span></span>  
  
6.  <span data-ttu-id="0e395-122">如果您選取**指定檔案名稱**，將字串值或內容屬性中的輸入**指定檔案名稱**欄位。</span><span class="sxs-lookup"><span data-stu-id="0e395-122">If you selected **Specify file name**, enter a string value or context property in the **Specify file name** field.</span></span> <span data-ttu-id="0e395-123">您也可以啟用**暫止訊息，如果找不到內容屬性 （如 %property%)** 來擱置訊息，如果選取的內容屬性不存在的傳出訊息。</span><span class="sxs-lookup"><span data-stu-id="0e395-123">You can also enable **Suspend message if context property (e.g. %property%) not found** to suspend the message if the selected context property does not exist for the outbound message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0e395-124">若要指定內容屬性，請用 %字元括住屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="0e395-124">To specify a context-property, enclose the property name with the % character.</span></span> <span data-ttu-id="0e395-125">例如， `%FILE.ReceivedFileName%`。</span><span class="sxs-lookup"><span data-stu-id="0e395-125">For example, `%FILE.ReceivedFileName%`.</span></span>  
  
7.  <span data-ttu-id="0e395-126">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0e395-126">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e395-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e395-127">See Also</span></span>  
 [<span data-ttu-id="0e395-128">設定本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="0e395-128">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)