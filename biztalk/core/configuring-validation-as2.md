---
title: 設定驗證 (AS2) |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1ff22dc8-a544-46f9-86fb-f6845e2dfe46
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c14d510f0d89a899aebf3feb308561aba2549df
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979783"
---
# <a name="configuring-validation-as2"></a><span data-ttu-id="0d41a-102">設定驗證 (AS2)</span><span class="sxs-lookup"><span data-stu-id="0d41a-102">Configuring Validation (AS2)</span></span>
<span data-ttu-id="0d41a-103">在夥伴協議中，您必須指定驗證設定來驗證輸入 AS2 訊息。</span><span class="sxs-lookup"><span data-stu-id="0d41a-103">In the partner agreement, you must specify the validation settings to validate the inbound AS2 message.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d41a-104">上的任何屬性會停用**合作對象 A]-> [合作對象 B**單向協議索引標籤，如果您清除**本機 BizTalk 可處理支援此合作對象傳送訊息的合作對象所接收的訊息**核取方塊合作對象 a。不過，下列屬性會停用在相同的頁面上**合作對象 B]-> [合作對象 A**索引標籤上，如果您在建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="0d41a-104">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, the following properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
>   
>  -   <span data-ttu-id="0d41a-105">**使用協議設定進行驗證，並以 MDN 取代訊息標頭**</span><span class="sxs-lookup"><span data-stu-id="0d41a-105">**Use agreement settings for validation and MDN instead of message header**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0d41a-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="0d41a-106">Prerequisites</span></span>  
 <span data-ttu-id="0d41a-107">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="0d41a-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-validation-properties"></a><span data-ttu-id="0d41a-108">設定驗證屬性</span><span class="sxs-lookup"><span data-stu-id="0d41a-108">To configure validation properties</span></span>  
  
1. <span data-ttu-id="0d41a-109">建立 AS2 協議中所述[設定的一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="0d41a-109">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="0d41a-110">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="0d41a-110">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2. <span data-ttu-id="0d41a-111">在單向協議索引標籤上，按一下 **驗證**。</span><span class="sxs-lookup"><span data-stu-id="0d41a-111">On a one-way agreement tab, click **Validation**.</span></span>  
  
3. <span data-ttu-id="0d41a-112">選取 **使用協議設定進行驗證與 MDN 取代訊息標頭**核取方塊，如果您想[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]驗證數位簽章、 壓縮和加密內送訊息，並根據中的設定協議。</span><span class="sxs-lookup"><span data-stu-id="0d41a-112">Select the **Use agreement settings for validation and MDN instead of message header** check box if you want [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] validate the digital signature, compression, and encryption of the incoming message, based upon the settings in the agreement.</span></span> <span data-ttu-id="0d41a-113">如果已清除此核取方塊，就會針對訊息 AS2 標頭中的屬性而不是針對協議屬性來驗證以判斷此處理。</span><span class="sxs-lookup"><span data-stu-id="0d41a-113">If the check box is cleared, the messages will be validated against the properties in the message AS2 header instead of the agreement properties to determine this processing.</span></span> <span data-ttu-id="0d41a-114">如需 AS2 標頭的清單，請參閱 < [AS2 訊息](../core/as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="0d41a-114">For a list of AS2 headers, see [AS2 Messages](../core/as2-messages.md).</span></span>  
  
4. <span data-ttu-id="0d41a-115">選取 **訊息應該簽署**核取方塊，以確保輸入的訊息已簽署。</span><span class="sxs-lookup"><span data-stu-id="0d41a-115">Select the **Message should be signed** check box to ensure that the inbound message is signed.</span></span>  
  
5. <span data-ttu-id="0d41a-116">選取 **訊息應該壓縮**核取方塊，以確保輸入的訊息已壓縮。</span><span class="sxs-lookup"><span data-stu-id="0d41a-116">Select the **Message should be compressed** check box to ensure that the inbound message is compressed.</span></span>  
  
6. <span data-ttu-id="0d41a-117">選取 **訊息應該加密**核取方塊，以確保輸入的訊息已加密。</span><span class="sxs-lookup"><span data-stu-id="0d41a-117">Select the **Message should be encrypted** check box to ensure that the inbound message is encrypted.</span></span> <span data-ttu-id="0d41a-118">選取的加密演算法**加密演算法**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="0d41a-118">Select the encryption algorithm from the **Encryption Algorithm** drop-down list.</span></span> 

   <span data-ttu-id="0d41a-119">**開頭[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]和較新版本**，AES 支援會自動包含。</span><span class="sxs-lookup"><span data-stu-id="0d41a-119">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] and newer versions**, AES support is automatically included.</span></span> <span data-ttu-id="0d41a-120">選項包括 DES3、 RC2，AES128 （預設）、 AES192、 和 AES256。</span><span class="sxs-lookup"><span data-stu-id="0d41a-120">Options include DES3, RC2, AES128 (default), AES192, and AES256.</span></span>
    
   <span data-ttu-id="0d41a-121">如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本中，選項會 DES3 和 RC2。</span><span class="sxs-lookup"><span data-stu-id="0d41a-121">For previous [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] versions, the options are DES3 and RC2.</span></span>
  
   > [!NOTE]
   >  <span data-ttu-id="0d41a-122">只有在已設定適當屬性時，AS2 接收管道才會驗證數位簽章、解壓縮訊息或解密訊息。</span><span class="sxs-lookup"><span data-stu-id="0d41a-122">Only if the appropriate property is set, the AS2 receive pipeline verifies the digital signature, decompresses the message, or decrypts the message.</span></span> <span data-ttu-id="0d41a-123">如果**使用協議設定進行驗證與 MDN 取代訊息標頭**選取屬性，而且該訊息的簽章、 壓縮和加密協議中選取不同的傳輸屬性屬性，則 AS2 解碼器會擱置訊息並發佈錯誤。</span><span class="sxs-lookup"><span data-stu-id="0d41a-123">If the **Use agreement settings for validation and MDN instead of message header** property is selected and the message has different transport properties for signing, compression, and encryption than those selected on the agreement properties, then the AS2 Decoder will suspend the message and post an error.</span></span>  
  
7. <span data-ttu-id="0d41a-124">選取 **檢查憑證撤銷清單**核取方塊，以判斷要用於驗證內送訊息的憑證是否已包含在憑證撤銷清單中，表示，它已被撤銷，或者，是否已經超過到期日。</span><span class="sxs-lookup"><span data-stu-id="0d41a-124">Select the **Check Certification Revocation List** check box to determine whether the certificate to be used in validating an incoming message has been included in the Certification Revocation List, indicating that it has been revoked, or whether the expiration date has passed.</span></span> <span data-ttu-id="0d41a-125">如果是的話，BizTalk Server 便不會解密訊息，但會擱置它。</span><span class="sxs-lookup"><span data-stu-id="0d41a-125">If so, BizTalk Server will not decrypt the message, but will suspend it.</span></span> <span data-ttu-id="0d41a-126">如果清除這個屬性，BizTalk Server 便不會執行這項檢查。</span><span class="sxs-lookup"><span data-stu-id="0d41a-126">If this property is cleared, BizTalk Server will not perform this check.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0d41a-127">在擷取和搜尋憑證撤銷清單時會發生延遲。</span><span class="sxs-lookup"><span data-stu-id="0d41a-127">There is a latency involved with retrieving and searching the certificate revocation list.</span></span>  
  
8. <span data-ttu-id="0d41a-128">選取 **檢查是否有重複的訊息內**核取方塊，以判斷內送訊息是否重複先前接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="0d41a-128">Select the **Check for duplicate messages within** check box to determine if the incoming message is a duplicate of previously received messages.</span></span>  
  
    <span data-ttu-id="0d41a-129">如果您已核取**檢查是否有重複的訊息內**屬性，設定**天**會複製屬性，指出先前接收的訊息時檢查所要使用的範圍，檢查**擱置重複訊息**屬性，以指示應暫止重複的訊息。</span><span class="sxs-lookup"><span data-stu-id="0d41a-129">If you checked the **Check for duplicate messages within** property, set the **days** property to indicate the span of previously received messages to use when checking for duplicates; check the **Suspend duplicate messages** property to indicate that duplicate messages should be suspended.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="0d41a-130">**AS2-從**並**AS2-以**欄位用來判斷訊息是否重複。</span><span class="sxs-lookup"><span data-stu-id="0d41a-130">The **AS2-From** and **AS2-To** fields are used to determine if a message is a duplicate.</span></span> <span data-ttu-id="0d41a-131">如果訊息包含與先前已接收訊息的這些欄位相同的值，即使其他標頭或內容不同，還是會標示為重複。</span><span class="sxs-lookup"><span data-stu-id="0d41a-131">If the message contains the same values for these fields as a previously received message, it will be marked as duplicate even if the other headers or the payload is different.</span></span>  
  
9. <span data-ttu-id="0d41a-132">按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0d41a-132">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d41a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d41a-133">See Also</span></span>  
 [<span data-ttu-id="0d41a-134">設定 AS2 協議屬性</span><span class="sxs-lookup"><span data-stu-id="0d41a-134">Configuring AS2 Agreement Properties</span></span>](../core/configuring-as2-agreement-properties.md)