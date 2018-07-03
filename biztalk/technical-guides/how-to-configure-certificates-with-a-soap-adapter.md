---
title: 如何設定 SOAP 配接器的憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 20ee05c5-9cea-456d-bff6-49dd249f0ff4
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0a709ab6b28796328677e7e8ae009e3273565a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012279"
---
# <a name="how-to-configure-certificates-with-a-soap-adapter"></a><span data-ttu-id="46547-102">如何設定 SOAP 配接器的憑證</span><span class="sxs-lookup"><span data-stu-id="46547-102">How to Configure Certificates with a SOAP Adapter</span></span>
<span data-ttu-id="46547-103">SOAP 傳送配接器可以協助保護與接受或要求用戶端憑證的伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="46547-103">The SOAP send adapter can help secure a connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="46547-104">若指定用戶端認證，則與要求或接收用戶端認證的伺服器連線時，SOAP 傳送配接器會使用認證。</span><span class="sxs-lookup"><span data-stu-id="46547-104">If you specify a client certificate, the SOAP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="46547-105">如果您未指定用戶端憑證和目的地伺服器需要用戶端憑證、 寄件者未經過驗證和 SOAP 傳送配接器無法傳送訊息，並依照標準重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="46547-105">If you do not specify a client certificate and the destination server requires client certificates, the sender is not authenticated and the SOAP send adapter fails to send the message and follows the standard retry logic.</span></span>  

 <span data-ttu-id="46547-106">SOAP 傳送配接器使用的用戶端憑證所使用的帳戶的個人存放區從[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理序正在執行。</span><span class="sxs-lookup"><span data-stu-id="46547-106">The SOAP send adapter uses the client certificate from the Personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="46547-107">SOAP 配接器會依照指紋來指定認證。</span><span class="sxs-lookup"><span data-stu-id="46547-107">The SOAP adapter specifies the certificate by its thumbprint.</span></span> <span data-ttu-id="46547-108">若 SOAP 傳送配接器因為任何原因而無法載入認證，它所傳送的訊息就會擱置。</span><span class="sxs-lookup"><span data-stu-id="46547-108">If the SOAP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  

 <span data-ttu-id="46547-109">當使用 SOAP 配接器來傳送加密或簽署訊息時，設定傳送埠的用戶端憑證指紋 SOAP 傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="46547-109">When using a SOAP adapter to send an encrypted or signed message, configure the Client Certificate Thumbprint SOAP transport property for the send port.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="46547-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="46547-110">Prerequisites</span></span>  
 <span data-ttu-id="46547-111">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="46547-111">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  

### <a name="to-configure-biztalk-server-to-send-messages-over-a-soap-connection"></a><span data-ttu-id="46547-112">若要設定透過 SOAP 連線傳送訊息的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="46547-112">To configure BizTalk Server to send messages over a SOAP connection</span></span>  

1. <span data-ttu-id="46547-113">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立新的 SOAP 傳送埠，或開啟現有的 SOAP 傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="46547-113">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new SOAP send port or open the properties for an existing SOAP send port.</span></span>  

2. <span data-ttu-id="46547-114">按一下 [**設定**中**傳輸**一節**傳送埠屬性**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="46547-114">Click **Configure** in the **Transport** section of the **Send Port Properties** dialog box.</span></span>  

3. <span data-ttu-id="46547-115">在上**一般**索引標籤中，於**驗證類型**，選取**Anonymous**，**基本**，**摘要**，或**NTLM**。</span><span class="sxs-lookup"><span data-stu-id="46547-115">On the **General** tab, in **Authentication type**, select **Anonymous**, **Basic**, **Digest**, or **NTLM**.</span></span>  

4. <span data-ttu-id="46547-116">驗證類型是否**基本**或**摘要**，選取**不會使用單一登入**（在此情況下您必須指定使用者名稱和密碼），或選取**使用單一登入**（在此情況下您必須選取分支機構應用程式）。</span><span class="sxs-lookup"><span data-stu-id="46547-116">If the authentication type is **Basic** or **Digest**, either select **Do not use Single Sign-On** (in which case you must specify the user name and password) or select **Use Single Sign-On** (in which case you must select the Affiliate Application).</span></span>  

5. <span data-ttu-id="46547-117">在  **SSL 用戶端憑證指紋**，輸入適當的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="46547-117">In **SSL client certificate thumbprint**, enter the appropriate thumbprint.</span></span>  

6. <span data-ttu-id="46547-118">按一下  **確定**，然後按一下**確定**一次。</span><span class="sxs-lookup"><span data-stu-id="46547-118">Click **OK**, and then click **OK** again.</span></span>
