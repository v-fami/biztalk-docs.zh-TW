---
title: 如何設定憑證與 HTTP 配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: dc2f454f-22b5-4113-9a23-e00a816d5e48
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f74b0a88983ede90899dac908a5407f8406ec1e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22297838"
---
# <a name="how-to-configure-certificates-with-an-http-adapter"></a><span data-ttu-id="a3b12-102">如何設定憑證與 HTTP 配接器</span><span class="sxs-lookup"><span data-stu-id="a3b12-102">How to Configure Certificates with an HTTP Adapter</span></span>
<span data-ttu-id="a3b12-103">HTTP 傳送配接器可以協助保護與接受或要求用戶端憑證的伺服器的連線。</span><span class="sxs-lookup"><span data-stu-id="a3b12-103">The HTTP send adapter can help secure a connection with servers that accept or require client certificates.</span></span> <span data-ttu-id="a3b12-104">若已指定用戶端憑證，則 HTTP 傳送配接器在與要求或接受用戶端憑證的伺服器連線時會使用憑證。</span><span class="sxs-lookup"><span data-stu-id="a3b12-104">If a client certificate is specified, the HTTP send adapter uses the certificate when connecting with servers that require or accept client certificates.</span></span> <span data-ttu-id="a3b12-105">如果未指定用戶端憑證，且目的地伺服器需要用戶端憑證，寄件者未經過驗證，HTTP 傳送配接器就無法傳送訊息，並依照標準重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="a3b12-105">If the client certificate is not specified and the destination server requires client certificates, the sender is not authenticated and the HTTP send adapter fails to send the message and follows the standard retry logic.</span></span>  
  
 <span data-ttu-id="a3b12-106">HTTP 傳送配接器會使用執行 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序的帳戶之個人存放區中的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="a3b12-106">The HTTP send adapter uses the client certificate from the personal store of the account under which the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process is running.</span></span> <span data-ttu-id="a3b12-107">憑證是由其指紋指定。</span><span class="sxs-lookup"><span data-stu-id="a3b12-107">The certificate is specified by its thumbprint.</span></span> <span data-ttu-id="a3b12-108">若 HTTP 傳送配接器因故無法載入憑證，則會擱置所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="a3b12-108">If the HTTP send adapter fails to load the certificate for any reason, the message that it was sending is suspended.</span></span>  
  
 <span data-ttu-id="a3b12-109">當使用 HTTP 配接器來傳送加密或簽署訊息時，設定 SSL 憑證指紋的傳送埠的 HTTP 傳輸屬性。</span><span class="sxs-lookup"><span data-stu-id="a3b12-109">When using an HTTP adapter to send an encrypted or signed message, configure the SSL certificate thumbprint HTTP transport property for the send port.</span></span> <span data-ttu-id="a3b12-110">在這個屬性，指定要用於訊息驗證憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="a3b12-110">In this property, specify the thumbprint of the certificate to use for message authentication.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a3b12-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="a3b12-111">Prerequisites</span></span>  
 <span data-ttu-id="a3b12-112">若要執行本主題中的程序，您必須登入的成員身分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="a3b12-112">To perform the procedure in this topic, you must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-configure-biztalk-server-to-send-messages-over-an-http-connection"></a><span data-ttu-id="a3b12-113">若要設定 BizTalk Server 透過 HTTP 連線傳送訊息</span><span class="sxs-lookup"><span data-stu-id="a3b12-113">To configure BizTalk Server to send messages over an HTTP connection</span></span>  
  
1.  <span data-ttu-id="a3b12-114">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，建立新的 HTTP 傳送埠，或開啟現有的 HTTP 傳送埠屬性。</span><span class="sxs-lookup"><span data-stu-id="a3b12-114">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, create a new HTTP send port or open the properties for an existing HTTP send port.</span></span>  
  
2.  <span data-ttu-id="a3b12-115">按一下**設定**中的 傳輸 區段**傳送埠屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a3b12-115">Click **Configure** in the Transport section of the **Send Port Properties** dialog box.</span></span>  
  
3.  <span data-ttu-id="a3b12-116">按一下**驗證**中**HTTP 傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a3b12-116">Click **Authentication** in the **HTTP Transport Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="a3b12-117">在**驗證類型**，選取**匿名**，**基本**，**摘要**，或**Kerberos**。</span><span class="sxs-lookup"><span data-stu-id="a3b12-117">In **Authentication type**, select **Anonymous**, **Basic**, **Digest**, or **Kerberos**.</span></span>  
  
5.  <span data-ttu-id="a3b12-118">如果驗證類型為**基本**或**摘要**，選取**不會使用單一登入**（在此情況下您必須指定使用者名稱和密碼），或選取**使用單一登入**（在此情況下您必須選取分支機構應用程式）。</span><span class="sxs-lookup"><span data-stu-id="a3b12-118">If the authentication type is **Basic** or **Digest**, either select **Do not use Single Sign-On** (in which case you must specify the user name and password) or select **Use Single Sign-On** (in which case you must select the Affiliate Application).</span></span>  
  
6.  <span data-ttu-id="a3b12-119">在**SSL 用戶端憑證指紋**，輸入適當的憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="a3b12-119">In **SSL client certificate thumbprint**, enter the appropriate thumbprint.</span></span>  
  
7.  <span data-ttu-id="a3b12-120">按一下**確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="a3b12-120">Click **OK**, and then click **OK** again.</span></span>