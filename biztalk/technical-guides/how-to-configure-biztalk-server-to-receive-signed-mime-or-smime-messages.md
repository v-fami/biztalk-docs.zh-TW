---
title: 如何設定 BizTalk Server 來接收簽署 MIME 或 SMIME 訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50570257-7bb6-4ede-9026-873eefd06483
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88487fb96c89b8a611ab591223fa1820f70de1cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297814"
---
# <a name="how-to-configure-biztalk-server-to-receive-signed-mime-or-smime-messages"></a><span data-ttu-id="f486d-102">如何設定 BizTalk Server 來接收簽署 MIME 或 SMIME 訊息</span><span class="sxs-lookup"><span data-stu-id="f486d-102">How to Configure BizTalk Server to Receive Signed MIME or SMIME Messages</span></span>
<span data-ttu-id="f486d-103">本主題描述如何設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]以使用憑證來接收簽署的 MIME/SMIME 訊息。</span><span class="sxs-lookup"><span data-stu-id="f486d-103">This topic describes how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to use certificates to receive signed MIME/SMIME messages.</span></span> <span data-ttu-id="f486d-104">下列程序也適用於透過 AS2 傳輸設定接收簽署的訊息。</span><span class="sxs-lookup"><span data-stu-id="f486d-104">The procedure below also applies to configuring the receiving of signed messages over AS2 transport.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f486d-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="f486d-105">Prerequisites</span></span>  
 <span data-ttu-id="f486d-106">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="f486d-106">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-receive-signed-messages"></a><span data-ttu-id="f486d-107">若要設定 BizTalk Server 來接收簽署的訊息</span><span class="sxs-lookup"><span data-stu-id="f486d-107">To configure BizTalk Server to receive signed messages</span></span>  
  
1.  <span data-ttu-id="f486d-108">建立管線來接收簽署的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f486d-108">Create a pipeline to receive signed messages, as follows:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f486d-109">設定 AS2 傳輸接收簽署的訊息，因為 AS2Receive 和 AS2EdiReceive 管線，在中時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]做這個函式。</span><span class="sxs-lookup"><span data-stu-id="f486d-109">This step is not necessary when configuring AS2 transport for receiving signed messages because the AS2Receive and AS2EdiReceive pipelines that are included in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] serve this function.</span></span>  
  
    1.  <span data-ttu-id="f486d-110">建立接收管線，然後將 MIME/SMIME 解碼器管線元件拖曳至接收管線的 「 解碼 」 階段。</span><span class="sxs-lookup"><span data-stu-id="f486d-110">Create a receive pipeline and then drag the MIME/SMIME Decoder pipeline component into the Decode stage of the receive pipeline.</span></span>  
  
    2.  <span data-ttu-id="f486d-111">在**屬性**視窗中，設定 MIME/SMIME 解碼器管線元件屬性。</span><span class="sxs-lookup"><span data-stu-id="f486d-111">In the **Properties** window, configure the MIME/SMIME Decoder pipeline component properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f486d-112">當您使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台將此管線部署到 BizTalk 群組後，您可以為接收位置設定管線屬性。</span><span class="sxs-lookup"><span data-stu-id="f486d-112">You can configure pipeline properties for a receive location after the pipeline has been deployed into a BizTalk group using the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="f486d-113">您可以針對 BizTalk 群組中的每一個接收位置設定不同的管線屬性。</span><span class="sxs-lookup"><span data-stu-id="f486d-113">You can configure different pipeline properties for each receive location in the BizTalk group.</span></span>  
  
    3.  <span data-ttu-id="f486d-114">建置和部署接收管線。</span><span class="sxs-lookup"><span data-stu-id="f486d-114">Build and deploy the receive pipeline.</span></span>  
  
2.  <span data-ttu-id="f486d-115">設定接收位置來接收簽署的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f486d-115">Configure a receive location for receiving signed messages, as follows:</span></span>  
  
    1.  <span data-ttu-id="f486d-116">將您建立包含 BizTalk 應用程式包括的接收位置來接收簽署的訊息的接收管線的 BizTalk 組件。</span><span class="sxs-lookup"><span data-stu-id="f486d-116">Add the BizTalk assembly that you created containing the receive pipeline to the BizTalk application including the receive locations to receive signed messages.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f486d-117">設定 AS2 傳輸接收簽署的訊息，因為在 「 BizTalk EDI 應用程式中包含 AS2Receive 和 AS2EdiReceive 管線時，不需要這個步驟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f486d-117">This step is not necessary when configuring AS2 transport for receiving signed messages because the AS2Receive and AS2EdiReceive pipelines are included in the BizTalk EDI Application in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
    2.  <span data-ttu-id="f486d-118">您在上一個程序中建立的接收管線的 BizTalk 應用程式中設定接收位置。</span><span class="sxs-lookup"><span data-stu-id="f486d-118">Configure the receive locations in the BizTalk application with the receive pipeline that you created in previous procedure.</span></span>  
  
3.  <span data-ttu-id="f486d-119">設定合作對象的憑證來接收簽署的訊息，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f486d-119">Configure the party with a certificate for receiving signed messages, as follows:</span></span>  
  
    -   <span data-ttu-id="f486d-120">開啟**合作對象屬性**對話方塊在 BizTalk Server 管理主控台中，按一下**憑證**索引標籤上，按一下 **瀏覽**，選取適當的憑證，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="f486d-120">Open the **Party Properties** dialog box in the BizTalk Server Administration Console, click the **Certificate** tab, click **Browse**, select the appropriate certificate, and then click **OK**.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="f486d-121">驗證某個合作對象的簽章時所使用的憑證，必須不同於驗證其他合作對象的簽章時所使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="f486d-121">The certificate used to verify a signature for a party must be unique from the certificates used to verify signatures for other parties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f486d-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f486d-122">See Also</span></span>  
 [<span data-ttu-id="f486d-123">設定 MIME 或 SMIME 訊息的憑證</span><span class="sxs-lookup"><span data-stu-id="f486d-123">Configuring Certificates for MIME or SMIME Messages</span></span>](../technical-guides/configuring-certificates-for-mime-or-smime-messages.md)