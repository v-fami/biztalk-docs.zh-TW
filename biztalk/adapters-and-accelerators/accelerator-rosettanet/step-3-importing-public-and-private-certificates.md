---
title: "步驟 3： 匯入公開憑證與私用憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public certificates
- importing certificates
- private certificates
- double action tutorial, importing certificates
- certificates, importing
ms.assetid: 955bdd69-9fbc-4100-ab8a-8f5dd4a17cbb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46d087c44cac350df2d58c880303668b5c3e0c24
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-importing-public-and-private-certificates"></a><span data-ttu-id="c4f14-102">步驟 3： 匯入公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="c4f14-102">Step 3: Importing Public and Private Certificates</span></span>
<span data-ttu-id="c4f14-103">在此步驟中，您匯入的憑證，您在建立[步驟 2： 建立公用和私用憑證 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) Contoso 和 Fabrikam 電腦。</span><span class="sxs-lookup"><span data-stu-id="c4f14-103">In this step, you import the certificates you created in [Step 2: Creating Public and Private Certificates &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) to the Contoso and Fabrikam computers.</span></span> <span data-ttu-id="c4f14-104">每台電腦都會匯入自己的私用憑證，並匯入其他組織的公開憑證。</span><span class="sxs-lookup"><span data-stu-id="c4f14-104">Each computer imports its own private certificates and imports the public certificates of the other organization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4f14-105">您必須將 Fabrikam 私用憑證和 Contoso 公開憑證傳送到 Fabrikam 電腦，才能匯入這些憑證。</span><span class="sxs-lookup"><span data-stu-id="c4f14-105">You have to transfer the Fabrikam private certificates and Contoso public certificates to the Fabrikam computer to import them.</span></span> <span data-ttu-id="c4f14-106">此步驟假設您將這些憑證放置在 Fabrikam 電腦的 C:\Certs 資料夾內。</span><span class="sxs-lookup"><span data-stu-id="c4f14-106">This step assumes that you put these certificates in the C:\Certs folder on the Fabrikam computer.</span></span>  
  
### <a name="to-import-the-contoso-private-certificates-on-the-contoso-computer"></a><span data-ttu-id="c4f14-107">在 Contoso 電腦上匯入 Contoso 私用憑證</span><span class="sxs-lookup"><span data-stu-id="c4f14-107">To import the Contoso private certificates on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="c4f14-108">在 Contoso 電腦上，按一下 **啟動**，按一下 **執行**，型別**cmd**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-108">On the Contoso computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c4f14-109">在命令提示字元中，移至 **\<** *磁碟機***\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK** ，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-109">At the command prompt, move to **\<***drive***\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="c4f14-110">在命令提示字元中，輸入**CertWizard /Privatekey"\<***磁碟機***\>: \Certs\Contoso Private Encryption.pfx"**，然後按下**輸入**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-110">At the command prompt, type **CertWizard /Privatekey "\<***drive***\>:\Certs\Contoso Private Encryption.pfx"**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="c4f14-111">在**請輸入憑證檔案的密碼**提示中，輸入**mysecret**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-111">At the **Please enter the password for the certificate file** prompt, type **mysecret**, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="c4f14-112">在**輸入密碼的身分識別 < contoso_machine > \HostSvc**提示，輸入 HostSvc 帳戶密碼，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-112">At the **Enter password for identity <contoso_machine>\HostSvc** prompt, type the HostSvc account password, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4f14-113">如果使用 HostSvc 以外的帳戶名稱來執行 BizTalkServerApplication，提示將會不同。</span><span class="sxs-lookup"><span data-stu-id="c4f14-113">If your BizTalkServerApplication runs under an account name other than HostSvc, the prompt must be different.</span></span>  
  
6.  <span data-ttu-id="c4f14-114">在**此主要憑證將用於**提示中，輸入**D**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-114">At the **This home certificate will be used for** prompt, type **D**, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="c4f14-115">CertWizard 會為執行 BizTalkServerApplication 及 BizTalkServerIsolatedHost 主控件的使用者帳戶，匯入憑證到 \Personal\Certificates 存放區。</span><span class="sxs-lookup"><span data-stu-id="c4f14-115">The CertWizard imports the certificate into the \Personal\Certificates store for the user accounts that BizTalkServerApplication and BizTalkServerIsolatedHost hosts run under.</span></span>  
  
7.  <span data-ttu-id="c4f14-116">重複步驟 3-6 Contoso Private Signature.pfx 憑證，指定它的簽章憑證是輸入**S**在**此主要憑證將用於**步驟 6 中的提示。</span><span class="sxs-lookup"><span data-stu-id="c4f14-116">Repeat steps 3-6 for the Contoso Private Signature.pfx certificate specifying that it is a signature certificate by typing **S** at the **This home certificate will be used for** prompt noted in step 6.</span></span>  
  
### <a name="to-import-the-fabrikam-public-certificates-on-the-contoso-computer"></a><span data-ttu-id="c4f14-117">在 Contoso 電腦上匯入 Fabrikam 公開憑證</span><span class="sxs-lookup"><span data-stu-id="c4f14-117">To import the Fabrikam public certificates on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="c4f14-118">在 Contoso 電腦上，按一下 **啟動**，按一下 **執行，**類型**cmd**，然後按一下  **確定**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-118">On the Contoso computer, click **Start**, click **Run,** type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c4f14-119">在命令提示字元中，移至*\<磁碟機\>***: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK**然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-119">At the command prompt, move to *\<drive\>***:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="c4f14-120">在命令提示字元中，輸入**CertWizard /Publickey"***\<磁碟機\>***: \Certs\Fabrikam Public Encryption.cer"**，然後按  **輸入**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-120">At the command prompt, type **CertWizard /Publickey "***\<drive\>***:\Certs\Fabrikam Public Encryption.cer"**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="c4f14-121">為 Fabrikam Public Signature.cer 憑證重複執行步驟 3。</span><span class="sxs-lookup"><span data-stu-id="c4f14-121">Repeat step 3 for the Fabrikam Public Signature.cer certificate.</span></span>  
  
### <a name="to-import-the-fabrikam-private-certificates-on-the-fabrikam-computer"></a><span data-ttu-id="c4f14-122">在 Fabrikam 電腦上匯入 Fabrikam 私用憑證</span><span class="sxs-lookup"><span data-stu-id="c4f14-122">To import the Fabrikam private certificates on the Fabrikam computer</span></span>  
  
1.  <span data-ttu-id="c4f14-123">將下列檔案複製至 Contoso 電腦\<磁碟機\>: Fabrikam 電腦上的 \Certs 資料夾： Contoso Public Encryption.cer、 Contoso Public Signature.cer、 Fabrikam Private Encryption.pfx 和 Fabrikam PrivateSignature.pfx。</span><span class="sxs-lookup"><span data-stu-id="c4f14-123">Copy the following files from the Contoso computer to the \<drive\>:\Certs folder on the Fabrikam computer: Contoso Public Encryption.cer, Contoso Public Signature.cer, Fabrikam Private Encryption.pfx, and Fabrikam Private Signature.pfx.</span></span>  
  
2.  <span data-ttu-id="c4f14-124">按一下 Fabrikum 電腦上，按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-124">On the Fabrikum computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c4f14-125">在命令提示字元中，移至*\<磁碟機\>***: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK**然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-125">At the command prompt, move to *\<drive\>***:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="c4f14-126">在命令提示字元中，輸入**CertWizard /Privatekey"***\<磁碟機\>***: \Certs\Fabrikam Private Encryption.pfx"**，然後按下**輸入**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-126">At the command prompt, type **CertWizard /Privatekey "***\<drive\>***:\Certs\Fabrikam Private Encryption.pfx"**, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="c4f14-127">在**請輸入憑證檔案的密碼**提示中，輸入**mysecret**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-127">At the **Please enter the password for the certificate file** prompt, type **mysecret**, and then press **Enter**.</span></span>  
  
6.  <span data-ttu-id="c4f14-128">在**輸入密碼的身分識別 < fabrikam_machine > \HostSvc**提示，輸入 HostSvc 帳戶密碼，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-128">At the **Enter password for identity <fabrikam_machine>\HostSvc** prompt, type the HostSvc account password, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c4f14-129">如果使用 HostSvc 以外的帳戶名稱來執行 BizTalkServerApplication，提示將會不同。</span><span class="sxs-lookup"><span data-stu-id="c4f14-129">If your BizTalkServerApplication runs under an account name other than HostSvc, the prompt must be different.</span></span>  
  
7.  <span data-ttu-id="c4f14-130">在**此主要憑證將用於**提示中，輸入**D**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-130">At the **This home certificate will be used for** prompt, type **D**, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="c4f14-131">CertWizard 會為執行 BizTalkServerApplication 及 BizTalkServerIsolatedHost 主控件的使用者帳戶，匯入憑證到 \Personal\Certificates 存放區。</span><span class="sxs-lookup"><span data-stu-id="c4f14-131">The CertWizard imports the certificate into the \Personal\Certificates store for the user accounts that BizTalkServerApplication and BizTalkServerIsolatedHost hosts run under.</span></span>  
  
8.  <span data-ttu-id="c4f14-132">重複步驟 4-7，Fabrikam Private Signature.pfx 憑證，指定它的簽章憑證輸入**S**在**此主要憑證將用於**提示在步驟 6。</span><span class="sxs-lookup"><span data-stu-id="c4f14-132">Repeat steps 4-7 for the Fabrikam Private Signature.pfx certificate specifying that it is a signature certificate by typing **S** at the **This home certificate will be used for** prompt in step 6.</span></span>  
  
### <a name="to-import-the-contoso-public-certificates-on-the-fabrikam-computer"></a><span data-ttu-id="c4f14-133">在 Fabrikam 電腦上匯入 Contoso 公開憑證</span><span class="sxs-lookup"><span data-stu-id="c4f14-133">To import the Contoso public certificates on the Fabrikam computer</span></span>  
  
1.  <span data-ttu-id="c4f14-134">按一下 Fabrikum 電腦上，按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-134">On the Fabrikum computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="c4f14-135">在命令提示字元中，移至*\<磁碟機\>***: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK**然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-135">At the command prompt, move to *\<drive\>***:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="c4f14-136">在命令提示字元中，輸入**CertWizard /Publickey"***\<磁碟機\>***: \Certs\Contoso Public Encryption.cer"**，然後按  **輸入**。</span><span class="sxs-lookup"><span data-stu-id="c4f14-136">At the command prompt, type **CertWizard /Publickey "***\<drive\>***:\Certs\Contoso Public Encryption.cer"**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="c4f14-137">為 Contoso Public Signature.cer 憑證重複執行步驟 3。</span><span class="sxs-lookup"><span data-stu-id="c4f14-137">Repeat step 3 for the Contoso Public Signature.cer certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4f14-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="c4f14-138">See Also</span></span>  
 [<span data-ttu-id="c4f14-139">步驟 4：在 IIS 中啟用安全通訊端層 (SSL)</span><span class="sxs-lookup"><span data-stu-id="c4f14-139">Step 4: Enabling Secure Sockets Layer in IIS</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)