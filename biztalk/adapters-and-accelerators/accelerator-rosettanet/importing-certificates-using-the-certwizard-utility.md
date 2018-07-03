---
title: 使用 CertWizard 公用程式匯入憑證 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, root keys
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- CertWizard utility
- certificates, importing
- root keys
ms.assetid: 0c54d7ab-69cf-4f4a-b976-6f740a41280b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50bdce5ff094153e0aaa0e6ca69b106993722722
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993799"
---
# <a name="importing-certificates-using-the-certwizard-utility"></a><span data-ttu-id="a4b2b-102">使用 CertWizard 公用程式匯入憑證</span><span class="sxs-lookup"><span data-stu-id="a4b2b-102">Importing Certificates Using the CertWizard Utility</span></span>
<span data-ttu-id="a4b2b-103">本主題描述如何使用 CertWizard 公用程式，逐步命令列公用程式可用於 Microsoft 匯入憑證[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]SDK。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-103">This topic describes how to import a certificate by using CertWizard utility, a step-by-step command-line utility available in the Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK.</span></span> <span data-ttu-id="a4b2b-104">此主題討論如何匯入私密、公開或根金鑰，</span><span class="sxs-lookup"><span data-stu-id="a4b2b-104">This topic discusses importing a private, public, or root key.</span></span> <span data-ttu-id="a4b2b-105">以及用來設定憑證的切換參數。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-105">It describes the switches that you use to configure the certificate.</span></span>  
  
 <span data-ttu-id="a4b2b-106">CertWizard 公用程式會自動執行許多步驟，您必須使用 Microsoft Management Console (MMC) 手動進行。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-106">The CertWizard utility automates many of the steps that you would have to do manually by using the Microsoft Management Console (MMC).</span></span> <span data-ttu-id="a4b2b-107">CertWizard 公用程式會執行**runas**命令來開啟 MMC，以主控件服務帳戶。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-107">The CertWizard utility performs the **runas** command to open MMC as the host service account.</span></span> <span data-ttu-id="a4b2b-108">如果您未新增**Useridentity**參數，它會偵測並使用主控件服務帳戶，提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-108">If you do not add a **Useridentity** switch, it will detect and use the host service account, prompting you for a password.</span></span> <span data-ttu-id="a4b2b-109">此公用程式亦可儲存與設定憑證。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-109">It stores and configures the certificate.</span></span>  
  
 <span data-ttu-id="a4b2b-110">您可以建立包含多個 CertWizard 公用程式命令的批次檔，以便同時匯入多個憑證。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-110">You can import multiple certificates at the same time by creating a batch file with multiple CertWizard utility commands.</span></span>  
  
### <a name="to-import-a-private-key"></a><span data-ttu-id="a4b2b-111">匯入私密金鑰</span><span class="sxs-lookup"><span data-stu-id="a4b2b-111">To import a private key</span></span>  
  
1. <span data-ttu-id="a4b2b-112">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-112">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="a4b2b-113">在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK** 。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-113">At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** .</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="a4b2b-114">使用 CertWizard 公用程式的說明，請輸入**CertWizard /？**</span><span class="sxs-lookup"><span data-stu-id="a4b2b-114">For help with the CertWizard utility, type **CertWizard /?**</span></span> <span data-ttu-id="a4b2b-115">在命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-115">at the command prompt.</span></span>  
  
3. <span data-ttu-id="a4b2b-116">在命令提示字元中，輸入**CertWizard /Privatekey\<檔名\>.pfx**，其中\< *filename*\>.pfx 包含私用憑證。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-116">At the command prompt, type **CertWizard /Privatekey \<filename\>.pfx**, where \<*filename*\>.pfx contains the private certificate.</span></span> <span data-ttu-id="a4b2b-117">若要提供檔案的密碼，將附加 **/Filepassword \<filepassword\>** 命令。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-117">To provide the password for the file, append **/Filepassword \<filepassword\>** to the command.</span></span>  
  
4. <span data-ttu-id="a4b2b-118">如果您想要將憑證匯入 BizTalk 主控件所使用的特定帳戶，附加 **/Useridentity \<useridentity\> /Password\<密碼\>** 命令。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-118">If you want to import the certificate into a specific account used by the BizTalk Host, append **/Useridentity \<useridentity\> /Password \<password\>** to the command.</span></span>  
  
5. <span data-ttu-id="a4b2b-119">如果您想要指定特定的憑證指紋，以防.pfx 檔案包含一個以上的憑證、 附加 **/Thumbprint\<指紋\>** 命令。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-119">If you want to designate a specific thumbprint in case the .pfx file contains more than one certificate, append **/Thumbprint \<thumbprint\>** to the command.</span></span>  
  
6. <span data-ttu-id="a4b2b-120">如果您想要設定憑證的使用方式，將附加 **/Usage**命令，然後附加下列值之一：</span><span class="sxs-lookup"><span data-stu-id="a4b2b-120">If you want to configure the usage of the certificate, append **/Usage** to the command, and then append one of the following values:</span></span>  
  
   -   <span data-ttu-id="a4b2b-121">附加**號**做為簽署憑證的憑證的指紋加入 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-121">Append **sign** to add the certificate's thumbprint as the signing certificate for the BizTalk Group.</span></span> <span data-ttu-id="a4b2b-122">在 BizTalk 管理主控台中的 Microsoft BizTalk server （本機） 對話方塊上設定。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-122">as set on the dialog box for Microsoft BizTalk Server (Local) in the BizTalk Administration Console.</span></span>  
  
   -   <span data-ttu-id="a4b2b-123">附加**解密**做為解密憑證加入憑證的指紋為 BizTalk 主控件中，為在 BizTalk 管理主控台中的每一部主機上的屬性頁的 [憑證] 索引標籤集合。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-123">Append **decrypt** to add the certificate's thumbprint as the decryption certificate for the BizTalk Hosts, as set on the certificate tab of the property pages for each host in the BizTalk Administration Console.</span></span>  
  
   -   <span data-ttu-id="a4b2b-124">附加**兩者**新增憑證的指紋，這兩個 BizTalk 群組的簽署憑證和 BizTalk 主控件的解密憑證。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-124">Append **both** to add the certificate's thumbprint for both the BizTalk Group's signing certificate and the BizTalk Host's decryption certificate.</span></span>  
  
   -   <span data-ttu-id="a4b2b-125">附加**無**時您不想設定 BizTalk 群組] 或 [BizTalk 主控件的設定。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-125">Append **none** when you do not want to set the configuration for the BizTalk Group or the BizTalk Hosts.</span></span>  
  
7. <span data-ttu-id="a4b2b-126">如果您想要將憑證設定為可匯出，附加 **/exportable true**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-126">If you want to configure the certificate as exportable, append **/Exportable true**.</span></span> <span data-ttu-id="a4b2b-127">若要將憑證設為不可匯出，附加 **/exportable false**，這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-127">To set the certificate as non-exportable, append **/Exportable false**, which is the default behavior.</span></span>  
  
8. <span data-ttu-id="a4b2b-128">按 **Enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-128">Press **Enter**.</span></span>  
  
9. <span data-ttu-id="a4b2b-129">若您未在命令中輸入所需密碼之一，工具會提示您輸入。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-129">If you did not type one of the passwords required in the command, the tool prompts you for it.</span></span> <span data-ttu-id="a4b2b-130">輸入密碼，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-130">Type the password, and then press **Enter**.</span></span>  
  
10. <span data-ttu-id="a4b2b-131">若檔案包含多個憑證，但您未在命令中輸入憑證指紋，工具將顯示可用的憑證指紋，並提示您選取其中一個憑證指紋。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-131">If the file contains multiple certificates, but you did not type a thumbprint in the command, the tool displays the available thumbprints, and prompts you to select one.</span></span> <span data-ttu-id="a4b2b-132">輸入的數目，然後再按下的憑證指紋**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-132">Type the number of the thumbprint that you want, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="a4b2b-133">此工具將憑證匯入 \Personal\Certificates 存放區中指定的使用者 **/useridentity**切換。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-133">The tool imports the certificate into the \Personal\Certificates store for the user specified in the **/useridentity** switch.</span></span> <span data-ttu-id="a4b2b-134">若您未指定使用者，則預設使用者為 BizTalkServerApplication 與 BizTalkServerIsolatedHost 主控件的使用者身份識別。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-134">If you do not specify a user, the default user is the user identity for the BizTalkServerApplication and BizTalkServerIsolatedHost hosts.</span></span>  
  
### <a name="to-import-a-public-key"></a><span data-ttu-id="a4b2b-135">匯入公開金鑰</span><span class="sxs-lookup"><span data-stu-id="a4b2b-135">To import a public key</span></span>  
  
1. <span data-ttu-id="a4b2b-136">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-136">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="a4b2b-137">在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾中的，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-137">At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder by using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.</span></span>  
  
3. <span data-ttu-id="a4b2b-138">在命令提示字元中，輸入**CertWizard /Publickey\<檔名\>.cer**，其中\< *filename*\>.cer 包含公開憑證。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-138">At the command prompt, type **CertWizard /Publickey \<filename\>.cer**, where \<*filename*\>.cer contains the public certificate.</span></span>  
  
4. <span data-ttu-id="a4b2b-139">如果您想要指定憑證的.cer 或.der 檔案中的憑證指紋，附加 **/Thumbprint\<指紋\>** 命令。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-139">If you want to designate a thumbprint for the certificate in the .cer or .der file, append **/Thumbprint \<thumbprint\>** to the command.</span></span>  
  
    <span data-ttu-id="a4b2b-140">這個工具會將憑證匯入 [憑證 (本機電腦)]\Other People\Certificates 存放區，並設定其組態。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-140">The tool imports the certificate into the Certificates (Local Computer)\Other People\Certificates store, and sets its configuration.</span></span>  
  
### <a name="to-import-a-root-key"></a><span data-ttu-id="a4b2b-141">匯入根金鑰</span><span class="sxs-lookup"><span data-stu-id="a4b2b-141">To import a root key</span></span>  
  
1. <span data-ttu-id="a4b2b-142">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-142">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="a4b2b-143">在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾中的，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK**。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-143">At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder by using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.</span></span>  
  
3. <span data-ttu-id="a4b2b-144">在命令提示字元中，輸入**CertWizard /Rootkey\<檔名\>.cer**，其中\< *filename*\>.cer 包含根憑證。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-144">At the command prompt, type **CertWizard /Rootkey \<filename\>.cer**, where \<*filename*\>.cer contains the root certificate.</span></span>  
  
4. <span data-ttu-id="a4b2b-145">如果您想要指定憑證的.cer 或.der 檔案中的憑證指紋，附加 **/Thumbprint\<指紋\>** 命令。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-145">If you want to designate a thumbprint for the certificate in the .cer or .der file, append **/Thumbprint \<thumbprint\>** to the command.</span></span>  
  
    <span data-ttu-id="a4b2b-146">這個工具會將憑證匯入 [憑證 (本機電腦)]\Trusted Root Certification Authority\Certificates 存放區，並設定其組態。</span><span class="sxs-lookup"><span data-stu-id="a4b2b-146">The tool imports the certificate into the Certificates (Local Computer)\Trusted Root Certification Authority\Certificates store, and sets its configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b2b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4b2b-147">See Also</span></span>  
 <span data-ttu-id="a4b2b-148">[CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md) </span><span class="sxs-lookup"><span data-stu-id="a4b2b-148">[CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md) </span></span>  
 [<span data-ttu-id="a4b2b-149">管理憑證</span><span class="sxs-lookup"><span data-stu-id="a4b2b-149">Managing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)