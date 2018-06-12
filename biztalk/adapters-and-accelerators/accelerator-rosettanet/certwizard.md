---
title: CertWizard |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, CertWizard utility
- CertWizard utility
- certificates, importing
ms.assetid: beeab3c0-d7b1-4bb9-8b19-f79b049d5aa1
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2aa2f9dd1edc9a3541b3b0d9c9a2efe2dbbe6931
ms.sourcegitcommit: 436ebffd959a9c4bdaafd4da9a5843c59a018eb7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2018
ms.locfileid: "34855633"
---
# <a name="certwizard"></a><span data-ttu-id="d2965-102">CertWizard</span><span class="sxs-lookup"><span data-stu-id="d2965-102">CertWizard</span></span>
<span data-ttu-id="d2965-103">您可使用 CertWizard 公用程式從 .pfx 或 .cer 檔案將憑證匯入到私用或公用存放區，以搭配 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 使用。</span><span class="sxs-lookup"><span data-stu-id="d2965-103">You use the CertWizard utility to import a certificate from a .pfx or .cer file into a private or public store for use with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="d2965-104">SDK 中的位置</span><span class="sxs-lookup"><span data-stu-id="d2965-104">Location in SDK</span></span>  
 <span data-ttu-id="d2965-105">\<*磁碟機*\>\Program Files (x86)\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for RosettaNet\SDK\\</span><span class="sxs-lookup"><span data-stu-id="d2965-105">\<*drive*\>\Program Files (x86)\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\</span></span>  
  
## <a name="running-certwizard"></a><span data-ttu-id="d2965-106">執行 CertWizard</span><span class="sxs-lookup"><span data-stu-id="d2965-106">Running CertWizard</span></span>  
  
#### <a name="to-run-certwizard"></a><span data-ttu-id="d2965-107">若要執行 CertWizard</span><span class="sxs-lookup"><span data-stu-id="d2965-107">To run CertWizard</span></span>  
  
1.  <span data-ttu-id="d2965-108">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d2965-108">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="d2965-109">移至\<*磁碟機*\>\ Program Files (x86)\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for RosettaNet\SDK\\。</span><span class="sxs-lookup"><span data-stu-id="d2965-109">Move to \<*drive*\>\ Program Files (x86)\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span></span>  
  
3.  <span data-ttu-id="d2965-110">在命令提示字元中，輸入**CertWizard**，輸入必要和適當的參數，然後按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="d2965-110">At the command prompt, type **CertWizard**, type the required and appropriate switches, and then press ENTER.</span></span>  
  
## <a name="syntax-for-certwizard"></a><span data-ttu-id="d2965-111">CertWizard 的語法</span><span class="sxs-lookup"><span data-stu-id="d2965-111">Syntax for CertWizard</span></span>  
 <span data-ttu-id="d2965-112">以下顯示您可用來啟動此命令列公用程式的語法：</span><span class="sxs-lookup"><span data-stu-id="d2965-112">The following shows the syntax that you use to start this command-line utility:</span></span>  
  
### <a name="syntax-for-importing-a-private-key"></a><span data-ttu-id="d2965-113">匯入私密金鑰的語法</span><span class="sxs-lookup"><span data-stu-id="d2965-113">Syntax for Importing a Private Key</span></span>  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
### <a name="syntax-for-importing-a-public-key"></a><span data-ttu-id="d2965-114">匯入公開金鑰的語法</span><span class="sxs-lookup"><span data-stu-id="d2965-114">Syntax for Importing a Public Key</span></span>  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-for-importing-a-root-key"></a><span data-ttu-id="d2965-115">匯入根金鑰的語法</span><span class="sxs-lookup"><span data-stu-id="d2965-115">Syntax for Importing a Root Key</span></span>  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="d2965-116">語法描述</span><span class="sxs-lookup"><span data-stu-id="d2965-116">Syntax Description</span></span>  
 <span data-ttu-id="d2965-117">下表描述 CertWizard 公用程式使用之語法的每個部分。</span><span class="sxs-lookup"><span data-stu-id="d2965-117">The following table describes each part of the syntax that the CertWizard utility uses.</span></span>  
  
|<span data-ttu-id="d2965-118">**語法**</span><span class="sxs-lookup"><span data-stu-id="d2965-118">**Syntax**</span></span>|<span data-ttu-id="d2965-119">**說明**</span><span class="sxs-lookup"><span data-stu-id="d2965-119">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="d2965-120">**Privatekey**</span><span class="sxs-lookup"><span data-stu-id="d2965-120">**Privatekey**</span></span>|<span data-ttu-id="d2965-121">用來匯入私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="d2965-121">Used to import a private key.</span></span>|  
|<span data-ttu-id="d2965-122">**Publickey**</span><span class="sxs-lookup"><span data-stu-id="d2965-122">**Publickey**</span></span>|<span data-ttu-id="d2965-123">用來匯入公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="d2965-123">Used to import a public key.</span></span>|  
|<span data-ttu-id="d2965-124">**Rootkey**</span><span class="sxs-lookup"><span data-stu-id="d2965-124">**Rootkey**</span></span>|<span data-ttu-id="d2965-125">用來匯入根金鑰—從憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="d2965-125">Used to import a root key—from a certification authority.</span></span>|  
|<span data-ttu-id="d2965-126">**filename.pfx （或.cer）**</span><span class="sxs-lookup"><span data-stu-id="d2965-126">**filename.pfx (or .cer)**</span></span>|<span data-ttu-id="d2965-127">.pfx (私密金鑰) 或 .cer (公開金鑰) 檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="d2965-127">Full path for the .pfx (private keys) or .cer (public keys) file.</span></span>|  
|<span data-ttu-id="d2965-128">**Filepassword**</span><span class="sxs-lookup"><span data-stu-id="d2965-128">**Filepassword**</span></span>|<span data-ttu-id="d2965-129">解除鎖定 .pfx 檔案所需的密碼。</span><span class="sxs-lookup"><span data-stu-id="d2965-129">The password required to unlock the .pfx file.</span></span>|  
|<span data-ttu-id="d2965-130">**Useridentity**</span><span class="sxs-lookup"><span data-stu-id="d2965-130">**Useridentity**</span></span>|<span data-ttu-id="d2965-131">一或多個 BizTalk 主控件使用的服務識別。</span><span class="sxs-lookup"><span data-stu-id="d2965-131">A service identity that one or more BizTalk Hosts uses.</span></span> <span data-ttu-id="d2965-132">如果您不想指定主控件，但想在使用者帳戶下匯入憑證，請輸入使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="d2965-132">Enter a user account if you do not want to specify the host, but want to import a certificate under a user account.</span></span> <span data-ttu-id="d2965-133">**注意：** 如果您需要新增**Useridentity**切換，公用程式匯入，並針對所有使用者設定的憑證。</span><span class="sxs-lookup"><span data-stu-id="d2965-133">**Note:**  If you do not add the **Useridentity** switch, the utility imports and set the certificate for all users.</span></span> <span data-ttu-id="d2965-134">**注意：** 如果您將加入**Useridentity**參數，但未輸入值，WMI 會自動產生使用者識別。</span><span class="sxs-lookup"><span data-stu-id="d2965-134">**Note:**  If you add the **Useridentity** switch, but do not enter a value, WMI automatically generates the user identity.</span></span>|  
|<span data-ttu-id="d2965-135">**密碼**</span><span class="sxs-lookup"><span data-stu-id="d2965-135">**Password**</span></span>|<span data-ttu-id="d2965-136">服務識別使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="d2965-136">The password for the service identity user.</span></span>|  
|<span data-ttu-id="d2965-137">**憑證指紋**</span><span class="sxs-lookup"><span data-stu-id="d2965-137">**Thumbprint**</span></span>|<span data-ttu-id="d2965-138">特定憑證的指紋，以防檔案包含一個以上的憑證。</span><span class="sxs-lookup"><span data-stu-id="d2965-138">The thumbprint of a specific certificate, in case the file contains more than one certificate.</span></span> <span data-ttu-id="d2965-139">**注意：** 公開憑證檔案，如果該檔案包含一個以上的憑證，且您未指定指紋，此公用程式匯入檔案中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="d2965-139">**Note:**  For a public certificate file, if the file contains more than one certificate and you do not specify the thumbprint, the utility imports all certificates in the file.</span></span> <span data-ttu-id="d2965-140">對於私用憑證檔案，此公用程式會提示您選取要匯入的憑證。</span><span class="sxs-lookup"><span data-stu-id="d2965-140">For a private certificate file, the utility prompts you to select the certificate to import.</span></span>|  
|<span data-ttu-id="d2965-141">**Usage**</span><span class="sxs-lookup"><span data-stu-id="d2965-141">**Usage**</span></span>|<span data-ttu-id="d2965-142">匯入之私用憑證的用途。</span><span class="sxs-lookup"><span data-stu-id="d2965-142">The intended usage of the imported private certificate.</span></span> <span data-ttu-id="d2965-143">可為 sign (對於簽章憑證)、decrypt (對於解密憑證)、both (對於同時是簽章憑證又是解密憑證的憑證)，或 none (也是對於同時是簽章憑證又是解密憑證的憑證)。</span><span class="sxs-lookup"><span data-stu-id="d2965-143">Can be sign (for a signing certificate), decrypt (for a decryption certificate), both (for a certificate that is both a signing certificate and a decryption certificate), or none (also for a certificate that is both a signing certificate and a decryption certificate).</span></span> <span data-ttu-id="d2965-144">**注意：** 如果您設定 **/Usage**參數設為 none，精靈就不在的 BizTalk 主控件或 BizTalk 群組上設定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="d2965-144">**Note:**  If you set the **/Usage** switch to none, the wizard will not set the thumbprint for the certificate on the BizTalk Hosts or the BizTalk Group.</span></span>|  
|<span data-ttu-id="d2965-145">**可匯出**</span><span class="sxs-lookup"><span data-stu-id="d2965-145">**Exportable**</span></span>|<span data-ttu-id="d2965-146">它可以是 `True` 或 `False`。</span><span class="sxs-lookup"><span data-stu-id="d2965-146">Can be `True` or `False`.</span></span> <span data-ttu-id="d2965-147">如果是 `True`，私密金鑰可能會再匯出一次。</span><span class="sxs-lookup"><span data-stu-id="d2965-147">If `True`, the private key can be re-exported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2965-148">備註</span><span class="sxs-lookup"><span data-stu-id="d2965-148">Remarks</span></span>  
 <span data-ttu-id="d2965-149">CertWizard 會從 .pfx file 檔案將私密金鑰匯入到個人存放區，從 .cer 檔案將公開金鑰匯入到公用存放區。</span><span class="sxs-lookup"><span data-stu-id="d2965-149">CertWizard imports a private key from a .pfx file into the personal store, and imports a public key from a .cer file into a public store.</span></span> <span data-ttu-id="d2965-150">匯入私密金鑰時，可對內送訊息使用解密憑證，對外送訊息使用簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="d2965-150">When importing a private key, the certificate can be a decryption certificate for incoming messages or a signing certificate for outgoing messages.</span></span>  
  
 <span data-ttu-id="d2965-151">如果您未在命令提示字元中提供完整的命令，CertWizard 會提示您輸入所需的值。</span><span class="sxs-lookup"><span data-stu-id="d2965-151">If you do not give the full command at the command prompt, CertWizard will prompt you to provide the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2965-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2965-152">See Also</span></span>  
 <span data-ttu-id="d2965-153">[公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span><span class="sxs-lookup"><span data-stu-id="d2965-153">[Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span></span>  
 [<span data-ttu-id="d2965-154">使用 CertWizard 公用程式匯入憑證</span><span class="sxs-lookup"><span data-stu-id="d2965-154">Importing Certificates Using the CertWizard Utility</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)
