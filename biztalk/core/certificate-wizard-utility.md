---
title: 憑證精靈公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ff72810-c7b3-4f67-8f9f-e127eacc153e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184056b6904b38945de836f04008b4a6fe90436a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970601"
---
# <a name="certificate-wizard-utility"></a><span data-ttu-id="b6e12-102">憑證精靈公用程式</span><span class="sxs-lookup"><span data-stu-id="b6e12-102">Certificate Wizard Utility</span></span>
<span data-ttu-id="b6e12-103">您可以使用 CertWizard 公用程式從.pfx 或.cer 檔案匯入憑證到私用或公用存放區，以搭配 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b6e12-103">You use the CertWizard utility to import a certificate from a .pfx or .cer file into a private or public store for use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="b6e12-104">憑證精靈 的原始程式碼可在**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Utilities\Certificate 精靈**資料夾。</span><span class="sxs-lookup"><span data-stu-id="b6e12-104">The source code for the Certificate Wizard can be found in the **C:\Program Files\Microsoft BizTalk Server \<version\>\SDK\Utilities\Certificate Wizard** folder.</span></span> <span data-ttu-id="b6e12-105">使用 64 位元作業系統與版本的 BizTalk Server 中，它會在**C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\SDK\Utilities\Certificate 精靈**資料夾。</span><span class="sxs-lookup"><span data-stu-id="b6e12-105">With a 64-bit operating system and version of BizTalk Server, it will be in the **C:\Program Files (x86)\Microsoft BizTalk Server \<version\>\SDK\Utilities\Certificate Wizard** folder.</span></span> <span data-ttu-id="b6e12-106">若要使用 [憑證精靈]，您就必須先使用 Visual Studio 建置它。</span><span class="sxs-lookup"><span data-stu-id="b6e12-106">To use the Certificate Wizard you will first have to build it using Visual Studio.</span></span>  
  
 <span data-ttu-id="b6e12-107">CertWizard 會從 .pfx file 檔案將私密金鑰匯入到個人存放區，從 .cer 檔案將公開金鑰匯入到公用存放區。</span><span class="sxs-lookup"><span data-stu-id="b6e12-107">CertWizard imports a private key from a .pfx file into the personal store, and imports a public key from a .cer file into a public store.</span></span> <span data-ttu-id="b6e12-108">匯入私密金鑰時，可對內送訊息使用解密憑證，對外送訊息使用簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="b6e12-108">When importing a private key, the certificate can be a decryption certificate for incoming messages or a signing certificate for outgoing messages.</span></span>  
  
 <span data-ttu-id="b6e12-109">**語法描述**</span><span class="sxs-lookup"><span data-stu-id="b6e12-109">**Syntax Description**</span></span>  
  
 <span data-ttu-id="b6e12-110">下表描述 CertWizard 公用程式使用之語法的每個部分。</span><span class="sxs-lookup"><span data-stu-id="b6e12-110">The following table describes each part of the syntax that the CertWizard utility uses.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b6e12-111">語法</span><span class="sxs-lookup"><span data-stu-id="b6e12-111">Syntax</span></span>|<span data-ttu-id="b6e12-112">描述</span><span class="sxs-lookup"><span data-stu-id="b6e12-112">Description</span></span>|  
|<span data-ttu-id="b6e12-113">Privatekey</span><span class="sxs-lookup"><span data-stu-id="b6e12-113">Privatekey</span></span>|<span data-ttu-id="b6e12-114">用來匯入私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="b6e12-114">Used to import a private key.</span></span>|  
|<span data-ttu-id="b6e12-115">Publickey</span><span class="sxs-lookup"><span data-stu-id="b6e12-115">Publickey</span></span>|<span data-ttu-id="b6e12-116">用來匯入公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="b6e12-116">Used to import a public key.</span></span>|  
|<span data-ttu-id="b6e12-117">Rootkey</span><span class="sxs-lookup"><span data-stu-id="b6e12-117">Rootkey</span></span>|<span data-ttu-id="b6e12-118">用來匯入根金鑰—從憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="b6e12-118">Used to import a root key—from a certification authority.</span></span>|  
|<span data-ttu-id="b6e12-119">filename.pfx (或 .cer)</span><span class="sxs-lookup"><span data-stu-id="b6e12-119">filename.pfx (or .cer)</span></span>|<span data-ttu-id="b6e12-120">.pfx (私密金鑰) 或 .cer (公開金鑰) 檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="b6e12-120">Full path for the .pfx (private keys) or .cer (public keys) file.</span></span>|  
|<span data-ttu-id="b6e12-121">Filepassword</span><span class="sxs-lookup"><span data-stu-id="b6e12-121">Filepassword</span></span>|<span data-ttu-id="b6e12-122">解除鎖定 .pfx 檔案所需的密碼。</span><span class="sxs-lookup"><span data-stu-id="b6e12-122">The password required to unlock the .pfx file.</span></span>|  
|<span data-ttu-id="b6e12-123">Useridentity</span><span class="sxs-lookup"><span data-stu-id="b6e12-123">Useridentity</span></span>|<span data-ttu-id="b6e12-124">一或多個 BizTalk 主控件使用的服務識別。</span><span class="sxs-lookup"><span data-stu-id="b6e12-124">A service identity that one or more BizTalk Hosts uses.</span></span> <span data-ttu-id="b6e12-125">如果您不想指定主控件，但想在使用者帳戶下匯入憑證，請輸入使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="b6e12-125">Enter a user account if you do not want to specify the host, but want to import a certificate under a user account.</span></span> <span data-ttu-id="b6e12-126">**注意：** 如果您未加入 Useridentity 參數，此公用程式匯入，並針對所有使用者設定的憑證。</span><span class="sxs-lookup"><span data-stu-id="b6e12-126">**Note:**  If you do not add the Useridentity switch, the utility imports and set the certificate for all users.</span></span> <span data-ttu-id="b6e12-127">**注意：** 如果您加入 Useridentity 參數，但不是輸入值，WMI 就會自動產生使用者識別。</span><span class="sxs-lookup"><span data-stu-id="b6e12-127">**Note:**  If you add the Useridentity switch, but do not enter a value, WMI automatically generates the user identity.</span></span>|  
|<span data-ttu-id="b6e12-128">[密碼]</span><span class="sxs-lookup"><span data-stu-id="b6e12-128">Password</span></span>|<span data-ttu-id="b6e12-129">服務識別使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="b6e12-129">The password for the service identity user.</span></span>|  
|<span data-ttu-id="b6e12-130">指模</span><span class="sxs-lookup"><span data-stu-id="b6e12-130">Thumbprint</span></span>|<span data-ttu-id="b6e12-131">特定憑證的指紋，以防檔案包含一個以上的憑證。</span><span class="sxs-lookup"><span data-stu-id="b6e12-131">The thumbprint of a specific certificate, in case the file contains more than one certificate.</span></span> <span data-ttu-id="b6e12-132">**注意：** 公開憑證檔案，如果檔案包含一個以上的憑證，而且您未指定指紋，此公用程式匯入檔案中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="b6e12-132">**Note:**  For a public certificate file, if the file contains more than one certificate and you do not specify the thumbprint, the utility imports all certificates in the file.</span></span> <span data-ttu-id="b6e12-133">對於私用憑證檔案，此公用程式會提示您選取要匯入的憑證。</span><span class="sxs-lookup"><span data-stu-id="b6e12-133">For a private certificate file, the utility prompts you to select the certificate to import.</span></span>|  
|<span data-ttu-id="b6e12-134">使用方式</span><span class="sxs-lookup"><span data-stu-id="b6e12-134">Usage</span></span>|<span data-ttu-id="b6e12-135">匯入之私用憑證的用途。</span><span class="sxs-lookup"><span data-stu-id="b6e12-135">The intended usage of the imported private certificate.</span></span> <span data-ttu-id="b6e12-136">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b6e12-136">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="b6e12-137">**登**（適用於簽章的憑證）</span><span class="sxs-lookup"><span data-stu-id="b6e12-137">**sign** (for a signing certificate)</span></span><br /><br /> <span data-ttu-id="b6e12-138">**解密**（對於解密憑證）</span><span class="sxs-lookup"><span data-stu-id="b6e12-138">**decrypt** (for a decryption certificate)</span></span><br /><br /> <span data-ttu-id="b6e12-139">**兩者**（適用於憑證所簽署的憑證和解密憑證）</span><span class="sxs-lookup"><span data-stu-id="b6e12-139">**both** (for a certificate that is both a signing certificate and a decryption certificate)</span></span><br /><br /> <span data-ttu-id="b6e12-140">**無**（也適用於憑證所簽署的憑證和解密憑證）。</span><span class="sxs-lookup"><span data-stu-id="b6e12-140">**none** (also for a certificate that is both a signing certificate and a decryption certificate).</span></span> <span data-ttu-id="b6e12-141">**注意：** 如果您將 /Usage 參數設為 none，精靈不會設定憑證的指紋 BizTalk 主控件或 BizTalk 群組上。</span><span class="sxs-lookup"><span data-stu-id="b6e12-141">**Note:**  If you set the /Usage switch to none, the wizard will not set the thumbprint for the certificate on the BizTalk Hosts or the BizTalk Group.</span></span>|  
|<span data-ttu-id="b6e12-142">Exportable</span><span class="sxs-lookup"><span data-stu-id="b6e12-142">Exportable</span></span>|<span data-ttu-id="b6e12-143">可以是**真**或是**False**。</span><span class="sxs-lookup"><span data-stu-id="b6e12-143">Can be **True** or **False**.</span></span> <span data-ttu-id="b6e12-144">如果 **，則為 True**，私密金鑰可以重複匯出。</span><span class="sxs-lookup"><span data-stu-id="b6e12-144">If **True**, the private key can be re-exported.</span></span>|  
  
 <span data-ttu-id="b6e12-145">**匯入私密金鑰的語法**</span><span class="sxs-lookup"><span data-stu-id="b6e12-145">**Syntax for Importing a Private Key**</span></span>  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
 <span data-ttu-id="b6e12-146">**匯入公開金鑰的語法**</span><span class="sxs-lookup"><span data-stu-id="b6e12-146">**Syntax for Importing a Public Key**</span></span>  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
 <span data-ttu-id="b6e12-147">**匯入根金鑰的語法**</span><span class="sxs-lookup"><span data-stu-id="b6e12-147">**Syntax for Importing a Root Key**</span></span>  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
## <a name="prerequisites"></a><span data-ttu-id="b6e12-148">必要條件</span><span class="sxs-lookup"><span data-stu-id="b6e12-148">Prerequisites</span></span>  
 <span data-ttu-id="b6e12-149">下列是執行本主題所述程序的必要條件：</span><span class="sxs-lookup"><span data-stu-id="b6e12-149">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
- <span data-ttu-id="b6e12-150">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="b6e12-150">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-run-the-certificate-wizard"></a><span data-ttu-id="b6e12-151">若要執行憑證精靈</span><span class="sxs-lookup"><span data-stu-id="b6e12-151">To run the certificate wizard</span></span>  
  
1. <span data-ttu-id="b6e12-152">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="b6e12-152">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="b6e12-153">移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities。</span><span class="sxs-lookup"><span data-stu-id="b6e12-153">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities.</span></span>  
  
3. <span data-ttu-id="b6e12-154">在命令提示字元中，輸入**CertWizard**，輸入必要和適當的參數，然後按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="b6e12-154">At the command prompt, type **CertWizard**, type the required and appropriate switches, and then press **Enter**.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="b6e12-155">如果您未在命令提示字元中提供完整的命令，CertWizard 會提示您輸入所需的值。</span><span class="sxs-lookup"><span data-stu-id="b6e12-155">If you do not give the full command at the command prompt, CertWizard will prompt you to provide the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e12-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e12-156">See Also</span></span>  
 [<span data-ttu-id="b6e12-157">SDK 中的公用程式</span><span class="sxs-lookup"><span data-stu-id="b6e12-157">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)