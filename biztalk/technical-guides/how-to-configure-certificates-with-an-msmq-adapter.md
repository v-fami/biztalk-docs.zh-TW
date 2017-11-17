---
title: "如何設定憑證與 MSMQ 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 922a171d-705f-4465-acda-212aa3797c57
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f36e3d13920982f79fe693a306a8123f089c76e2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-certificates-with-an-msmq-adapter"></a><span data-ttu-id="847b4-102">如何設定憑證與 MSMQ 配接器</span><span class="sxs-lookup"><span data-stu-id="847b4-102">How to Configure Certificates with an MSMQ Adapter</span></span>
<span data-ttu-id="847b4-103">MSMQ 傳送配接器可以協助保護與接受或要求用戶端憑證的伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="847b4-103">The MSMQ send adapter can help secure a connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="847b4-104">如果指定的用戶端憑證，則 MSMQ 傳送配接器與要求或接受用戶端憑證的伺服器連接時，就會使用的憑證。</span><span class="sxs-lookup"><span data-stu-id="847b4-104">If a client certificate is specified, the MSMQ send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="847b4-105">如果未指定用戶端憑證和目的地伺服器需要用戶端憑證，寄件者未經過驗證，而且 MSMQ 傳送配接器無法傳送訊息，並依照標準重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="847b4-105">If the client certificate is not specified and the destination server requires client certificates, the sender is not authenticated and the MSMQ send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="847b4-106">MSMQ 傳送配接器使用的用戶端憑證所使用的帳戶之個人存放區中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="847b4-106">The MSMQ send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="847b4-107">憑證是由其指紋指定。</span><span class="sxs-lookup"><span data-stu-id="847b4-107">The certificate is specified by its thumbprint.</span></span> <span data-ttu-id="847b4-108">如果 MSMQ 傳送配接器無法載入憑證，因為任何原因，它所傳送的訊息將遭擱置。</span><span class="sxs-lookup"><span data-stu-id="847b4-108">If the MSMQ send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
 <span data-ttu-id="847b4-109">當使用 MSMQ 配接器來傳送加密或簽署訊息時，設定傳送埠的憑證指紋 MSMQ 傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="847b4-109">When using an MSMQ adapter to send an encrypted or signed message, configure the Certificate Thumbprint MSMQ transport property for the send port.</span></span> <span data-ttu-id="847b4-110">在這個屬性，指定要用於訊息驗證憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="847b4-110">In this property, specify the thumbprint of the certificate to use for message authentication.</span></span> <span data-ttu-id="847b4-111">將此屬性與 [使用驗證] 屬性搭配使用以驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="847b4-111">Use this property in combination with the Use Authentication property to verify the message.</span></span> <span data-ttu-id="847b4-112">使用 [使用者名稱] 和 [密碼] 屬性以取得佇列的存取權。</span><span class="sxs-lookup"><span data-stu-id="847b4-112">Use the User Name and Password properties to gain access to queues.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="847b4-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="847b4-113">Prerequisites</span></span>  
 <span data-ttu-id="847b4-114">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="847b4-114">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-msmq-connection"></a><span data-ttu-id="847b4-115">設定要傳送訊息的 MSMQ 連接的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="847b4-115">To configure BizTalk Server to send messages over an MSMQ connection</span></span>  
  
1.  <span data-ttu-id="847b4-116">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立新的 MSMQ 傳送埠，或開啟現有的 MSMQ 傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="847b4-116">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new MSMQ send port or open the properties for an existing MSMQ send port.</span></span>  
  
2.  <span data-ttu-id="847b4-117">按一下**設定**中**傳輸**區段**傳送埠屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="847b4-117">Click **Configure** in the **Transport** section of the **Send Port Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="847b4-118">在**MSMQ 傳輸屬性**對話方塊中，針對**驗證**，選取**True**。</span><span class="sxs-lookup"><span data-stu-id="847b4-118">In the **MSMQ Transport Properties** dialog box, for **Authentication**, select **True**.</span></span>  
  
4.  <span data-ttu-id="847b4-119">如**憑證指紋**，輸入適當的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="847b4-119">For **Certificate thumbprint**, enter the appropriate thumbprint.</span></span>  
  
5.  <span data-ttu-id="847b4-120">按一下**確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="847b4-120">Click **OK**, and then click **OK** again.</span></span>