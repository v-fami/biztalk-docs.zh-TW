---
title: 設定接收者 MDN 設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eae6431d-a2b9-4889-a29c-720e801a644e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafe17a0ad357b840b31d8a10c67e1ae3cc1e415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233374"
---
# <a name="configuring-receiver-mdn-settings"></a><span data-ttu-id="cba15-102">設定接收者 MDN 設定</span><span class="sxs-lookup"><span data-stu-id="cba15-102">Configuring Receiver MDN Settings</span></span>
<span data-ttu-id="cba15-103">在接收者 MDN 設定中，您可以根據 AS2 訊息標頭，指定控制 MDN 產生方式的屬性。</span><span class="sxs-lookup"><span data-stu-id="cba15-103">As part of receiver MDN settings, you can specify the properties that govern MDN generation based on the AS2 message header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cba15-104">任何屬性已停用**合作對象 a-> 合作對象 B**單向協議索引標籤，如果您清除了**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊合作對象 a。不過，所有屬性已停都用中相同頁面**合作對象 B-> 合作對象 A**索引標籤上，如果您建立合作對象 a 時選取此核取方塊</span><span class="sxs-lookup"><span data-stu-id="cba15-104">No properties are disabled on **Party A->Party B** one-way agreement tab if you cleared the **Local BizTalk processes messages received by the party or supports sending messages from this party** check box for Party A. However, all the properties are disabled on the same page in the **Party B->Party A** tab if you selected the check box while creating Party A.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cba15-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="cba15-105">Prerequisites</span></span>  
 <span data-ttu-id="cba15-106">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="cba15-106">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
### <a name="to-configure-receiver-mdn-settings"></a><span data-ttu-id="cba15-107">若要設定接收者 MDN 設定</span><span class="sxs-lookup"><span data-stu-id="cba15-107">To configure receiver MDN settings</span></span>  
  
1.  <span data-ttu-id="cba15-108">建立 AS2 協議中所述[設定一般設定 (AS2)](../core/configuring-general-settings-as2.md)。</span><span class="sxs-lookup"><span data-stu-id="cba15-108">Create an AS2 agreement as described in [Configuring General Settings (AS2)](../core/configuring-general-settings-as2.md).</span></span> <span data-ttu-id="cba15-109">若要更新現有的 AS2 協議，以滑鼠右鍵按一下協議中的**合作對象與商務設定檔**頁面，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="cba15-109">To update an existing AS2 agreement, right-click the agreement in the **Parties and Business Profiles** page, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="cba15-110">在單向協議索引標籤底下**本機主機設定**區段中，按一下**接收者 MDN 設定**。</span><span class="sxs-lookup"><span data-stu-id="cba15-110">On a one-way agreement tab, under **Local Host Settings** section, click **Receiver MDN Settings**.</span></span>  
  
3.  <span data-ttu-id="cba15-111">如果您沒有勾選**對驗證與 MDN 使用協議設定，而非訊息標頭**屬性**驗證** 頁面上，您可以選擇讓傳送 MDN 的合作對象簽署 MDN，如果會啟用產生 MDN**配置通知至**AS2 標頭，但**配置通知選項**標頭沒有啟用簽署。</span><span class="sxs-lookup"><span data-stu-id="cba15-111">If you did not check the **Use agreement settings for validation and MDN instead of message header** property in the **Validations** page, you can choose to have the party sending the MDN, sign the MDN if generation of the MDN is enabled by the **Disposition-Notification-to** AS2 header, but the **Disposition-Notification-Options** header does not enable signing.</span></span> <span data-ttu-id="cba15-112">這種情形**配置通知選項**未設定或設定為選擇性。</span><span class="sxs-lookup"><span data-stu-id="cba15-112">This can occur if **Disposition-Notification-Options** is either not set or is set to optional.</span></span> <span data-ttu-id="cba15-113">您可以按一下**簽署要求的 MDN，如果不預設配置通知選項標頭，或簽署回條通訊協定標頭設定為選擇性**。</span><span class="sxs-lookup"><span data-stu-id="cba15-113">You can do so by clicking **Sign requested MDN if Disposition-Notification-Option header is not preset or if Signed-Receipt-Protocol header is set to optional**.</span></span>  
  
4.  <span data-ttu-id="cba15-114">您可以輸入中的文字**MDN 文字**讓傳送 MDN 將它加入至 MDN 訊息 （在 Content-description 欄位） 的合作對象的欄位。</span><span class="sxs-lookup"><span data-stu-id="cba15-114">You can enter a text in the **MDN Text** field to have the party sending the MDN add it to the MDN message (under the Content-Description field).</span></span> <span data-ttu-id="cba15-115">不論 MDN 是根據 AS2 標頭還是協議屬性來產生，都適用這個設定。</span><span class="sxs-lookup"><span data-stu-id="cba15-115">This setting is applicable irrespective of whether the MDN was generated based upon the AS2 headers or the agreement properties.</span></span>  
  
5.  <span data-ttu-id="cba15-116">按一下**套用**繼續進行組態之前接受變更，或按一下**確定**來驗證變更，然後關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="cba15-116">Click **Apply** to accept the changes before continuing with the configuration, or click **OK** to validate the changes and then close the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cba15-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cba15-117">See Also</span></span>  
 [<span data-ttu-id="cba15-118">設定本機主機設定 (AS2)</span><span class="sxs-lookup"><span data-stu-id="cba15-118">Configuring Local Host Settings (AS2)</span></span>](../core/configuring-local-host-settings-as2.md)