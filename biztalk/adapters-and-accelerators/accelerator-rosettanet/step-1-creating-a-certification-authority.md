---
title: "步驟 1： 建立憑證授權單位 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, creating
- double action tutorial, creating certificates
- creating, certificates
ms.assetid: b6ecd534-6b03-4336-8337-33ec18a0802a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94a2b02b654983701323703edcc1b3ba3fcca13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-a-certification-authority"></a><span data-ttu-id="a9ac0-102">步驟 1： 建立憑證授權單位</span><span class="sxs-lookup"><span data-stu-id="a9ac0-102">Step 1: Creating a Certification Authority</span></span>
<span data-ttu-id="a9ac0-103">在本主題中，您將安裝憑證服務 [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 元件。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-103">In this topic, you install the Certificate Services [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] component.</span></span> <span data-ttu-id="a9ac0-104">您可以使用此元件產生必要的憑證，以促成 Contoso 和 Fabrikam 組織之間的安全通訊。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-104">You use it to generate the certificates that you need to promote secure communication between the Contoso and Fabrikam organizations.</span></span> <span data-ttu-id="a9ac0-105">每個交易夥伴都會有可用來通訊的私人加密憑證，以及用於識別身份的私人簽章憑證。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-105">Each trading partner will have a private encryption certificate for communication and a private signature certificate for identification purposes.</span></span> <span data-ttu-id="a9ac0-106">此外，交易夥伴將彼此共用公開金鑰憑證，以便在實作 3A2 交易夥伴介面程序 (PIP) 時保護彼此之間的通訊。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-106">Additionally, the partners will share their public key certificates with each other to promote secure communication when implementing the 3A2 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-install-the-certificate-server"></a><span data-ttu-id="a9ac0-107">安裝憑證伺服器</span><span class="sxs-lookup"><span data-stu-id="a9ac0-107">To install the certificate server</span></span>  
  
1.  <span data-ttu-id="a9ac0-108">按一下**啟動**，指向 **設定**，然後按一下 **控制台**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-108">Click **Start**, point to **Settings**, and then click **Control Panel**.</span></span> <span data-ttu-id="a9ac0-109">按兩下**新增或移除程式**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-109">Double-click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="a9ac0-110">在**新增或移除程式**對話方塊中，按一下 **新增/移除 Windows 元件**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-110">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="a9ac0-111">上**Windows 元件精靈**頁面上，於**元件**區段中，選取**憑證服務**，按一下 **是**，然後按一下**下一步**啟動設定元件精靈。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-111">On the **Windows Components Wizard** page, in the **Components** section, select **Certificate Services**, click **Yes**, and then click **Next** to start the Configuring Components Wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9ac0-112">如果**憑證 ServicesWindows**元件已經選取，請略過此程序的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-112">If the **Certificates ServicesWindows** component is already selected, skip the rest of this procedure.</span></span>  
  
4.  <span data-ttu-id="a9ac0-113">在**CA 類型**頁面上，請確定**獨立根 CA**已選取，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-113">On the **CA Type** page, make sure that **Stand-alone root CA** is selected, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="a9ac0-114">在**CA 識別資訊**頁面上，於**此 CA 的一般名稱**方塊中，輸入**Contoso-fabrikamca**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-114">On the **CA Identifying Information** page, in the **Common name for this CA** box, type **Contoso-FabrikamCA**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="a9ac0-115">在**憑證資料庫設定**頁面上，保留預設值，然後按**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-115">On the **Certificate Database Settings** page, leave the defaults, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="a9ac0-116">按一下**是**時精靈會提示您停止 Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-116">Click **Yes** when the wizard prompts you to stop Internet Information Services (IIS).</span></span>  
  
8.  <span data-ttu-id="a9ac0-117">按一下**是**如果**設定元件精靈**會提示您啟用 Active Server Pages。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-117">Click **Yes** if the **Configuring Components Wizard** prompts you to enable Active Server Pages.</span></span>  
  
9. <span data-ttu-id="a9ac0-118">按一下**完成**關閉**Windows 元件精靈**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-118">Click **Finish** to close the **Windows Components Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9ac0-119">您只需要使用一台電腦做為憑證授權單位，</span><span class="sxs-lookup"><span data-stu-id="a9ac0-119">You only have to use one computer as the Certification Authority.</span></span> <span data-ttu-id="a9ac0-120">不必在另一台電腦上重複執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-120">You do not have to repeat this step on the second computer.</span></span> <span data-ttu-id="a9ac0-121">本教學課程使用 Contoso 電腦做為憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-121">This tutorial uses the Contoso computer as the Certification Authority.</span></span>  
  
### <a name="to-install-a-root-certification-authority-ca-for-windows-server-2008"></a><span data-ttu-id="a9ac0-122">若要安裝 Windows Server 2008 的根憑證授權單位 (CA)</span><span class="sxs-lookup"><span data-stu-id="a9ac0-122">To install a root Certification Authority (CA) for Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="a9ac0-123">開啟 伺服器管理員中，按一下**新增角色**在角色中，按一下 **下一步**，然後按一下**Active Directory 憑證**服務 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-123">Open Server Manager, click **Add Roles** in Roles, click **Next**, and click **Active Directory Certificate** Services check box.</span></span> <span data-ttu-id="a9ac0-124">按一下**下一步**兩次。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-124">Click **Next** twice.</span></span>  
  
2.  <span data-ttu-id="a9ac0-125">在 選取角色服務頁面上，按一下 **憑證授權單位和憑證授權單位網頁註冊**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-125">On the Select Role Services page, click **Certification Authority and Certification Authority Web Enrollment**.</span></span> <span data-ttu-id="a9ac0-126">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-126">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="a9ac0-127">在 指定安裝類型 頁面上，按一下 **獨立**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-127">On the Specify Setup Type page, click **Standalone**.</span></span> <span data-ttu-id="a9ac0-128">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-128">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="a9ac0-129">在 指定 CA 類型 頁面中，按一下 根 CA。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-129">On the Specify CA Type page, click Root CA.</span></span> <span data-ttu-id="a9ac0-130">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-130">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="a9ac0-131">在 [安裝私密金鑰] 頁面上，按一下 [建立新的私密金鑰]。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-131">On the Set Up Private Key page, click Create a new private key.</span></span> <span data-ttu-id="a9ac0-132">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-132">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="a9ac0-133">在 [設定 CA 的密碼編譯] 頁面上，</span><span class="sxs-lookup"><span data-stu-id="a9ac0-133">On the Configure Cryptography for CA page.</span></span> <span data-ttu-id="a9ac0-134">按一下 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-134">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="a9ac0-135">設定 CA 名稱 上的一般名稱，這個 CA 方塊中，輸入 Contoso-fabrikamca，，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-135">On Configure CA Name, in the Common name for this CA box, type Contoso-FabrikamCA, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="a9ac0-136">在 設定有效期間 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-136">On the Set Validity Period page, click **Next**.</span></span>  
  
9. <span data-ttu-id="a9ac0-137">在 設定憑證資料庫 頁面上，按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-137">On the Configure Certificate Database page, Click **Next**.</span></span>  
  
10. <span data-ttu-id="a9ac0-138">在 確認安裝選項 頁面上，按一下 **安裝**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-138">On the Confirm Installation Options page, click **Install**.</span></span>  
  
### <a name="configuring-the-web-site-for-the-ca-to-use-https-authentication"></a><span data-ttu-id="a9ac0-139">設定 CA 的網站使用 HTTPS 驗證</span><span class="sxs-lookup"><span data-stu-id="a9ac0-139">Configuring the Web site for the CA to use HTTPS authentication</span></span>  
  
1.  <span data-ttu-id="a9ac0-140">在您當做憑證授權單位使用的電腦上，按一下 [開始]，指向 [所有程式]，再指向 [系統管理工具]，然後按一下 [網際網路資訊服務 (IIS) 管理員]。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-140">On the computer you used as the Certification Authority, click Start, point to All Programs, point to Administrative Tools, and then click Internet Information Services (IIS) Manager.</span></span>  
  
2.  <span data-ttu-id="a9ac0-141">在 [網際網路資訊服務 (IIS) 管理員] 對話方塊中，以滑鼠右鍵按一下**預設的網站和選取編輯繫結...**</span><span class="sxs-lookup"><span data-stu-id="a9ac0-141">In the Internet Information Services (IIS) Manager dialog box, right click **Default Web Site and select Edit Bindings…**</span></span> <span data-ttu-id="a9ac0-142">從快顯功能表。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-142">from the popup menu.</span></span>  
  
3.  <span data-ttu-id="a9ac0-143">在站台繫結 對話方塊中按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-143">In Site Bindings dialog box click **Add**.</span></span>  
  
4.  <span data-ttu-id="a9ac0-144">在 新增網站繫結 對話方塊中選取**https**在 類型 下拉式清單，選取從憑證**SSL 憑證**下拉式清單，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-144">In Add Site Binding dialog box select **https** in Type drop down, select the certificate from **SSL certificate** drop down and click **OK**.</span></span>  
  
5.  <span data-ttu-id="a9ac0-145">按一下**關閉**關閉站台繫結...</span><span class="sxs-lookup"><span data-stu-id="a9ac0-145">Click **Close** to close the Site Bindings…</span></span> <span data-ttu-id="a9ac0-146">對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-146">dialog box.</span></span>  
  
### <a name="to-download-the-ca-certificate"></a><span data-ttu-id="a9ac0-147">若要下載 CA 憑證</span><span class="sxs-lookup"><span data-stu-id="a9ac0-147">To download the CA certificate</span></span>  
  
1.  <span data-ttu-id="a9ac0-148">在 Internet Explorer 中，找出並開啟 http://<contoso_computername>/certsrv/Default.asp。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-148">In Internet Explorer, locate and open http://<contoso_computername>/certsrv/Default.asp.</span></span>  
  
2.  <span data-ttu-id="a9ac0-149">在 Default.asp 頁面上，按一下 **下載 CA 憑證、 憑證鏈結或 CRL**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-149">On the Default.asp page, click **Download a CA certificate, certificate chain, or CRL**.</span></span>  
  
3.  <span data-ttu-id="a9ac0-150">請確定**目前 [Contoso-fabrikamca]**中選取**CA 憑證**清單，然後再按**下載 CA 憑證**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-150">Make sure that **Current[Contoso-FabrikamCA]** is selected in the **CA Certificate** list, and then click **Download CA Certificate**.</span></span>  
  
4.  <span data-ttu-id="a9ac0-151">在 Contoso 和 Fabrikam 電腦上都將憑證儲存為 C:\Certs\Contoso-FabrikamCA.cer。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-151">Save the certificate to C:\Certs\Contoso-FabrikamCA.cer on both the Contoso and the Fabrikam computer.</span></span>  
  
### <a name="to-import-the-ca-certificate-to-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="a9ac0-152">將 CA 憑證匯入至受信任的根憑證授權單位存放區</span><span class="sxs-lookup"><span data-stu-id="a9ac0-152">To import the CA certificate to the Trusted Root Certification Authorities store</span></span>  
  
1.  <span data-ttu-id="a9ac0-153">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-153">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="a9ac0-154">在命令提示字元中，移至**\<磁碟機 >: \Program Files\MicrosoftBizTalk\<版本 > Accelerator for RosettaNet\SDK**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-154">At the command prompt, move to **\<drive>:\Program Files\MicrosoftBizTalk \<version> Accelerator for RosettaNet\SDK**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="a9ac0-155">在命令提示字元中，輸入**CertWizard /Rootkey"\<磁碟機 >: \Certs\Contoso-FabrikamCA.cer"**，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-155">At the command prompt, type **CertWizard /Rootkey "\<drive>:\Certs\Contoso-FabrikamCA.cer"**, and then press **Enter**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a9ac0-156">在 Contoso 和 Fabrikam 兩台電腦執行此程序。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-156">Perform this procedure on both the Contoso and Fabrikam computers.</span></span>  
  
### <a name="to-enable-automatic-certificate-issuing"></a><span data-ttu-id="a9ac0-157">啟用自動憑證核發</span><span class="sxs-lookup"><span data-stu-id="a9ac0-157">To enable automatic certificate issuing</span></span>  
  
1.  <span data-ttu-id="a9ac0-158">在做為憑證授權單位的電腦，按一下**啟動**，指向 **程式**，指向 **系統管理工具**，然後按一下  **憑證授權單位**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-158">On the computer you used as the Certification Authority, click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Certification Authority**.</span></span>  
  
2.  <span data-ttu-id="a9ac0-159">在 憑證授權單位 對話方塊中，以滑鼠右鍵按一下**Contoso-fabrikamca**，然後按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-159">In the Certification Authority dialog box, right-click **Contoso-FabrikamCA**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="a9ac0-160">在 Contoso-fabrikamca 內容 對話方塊上**原則模組**索引標籤上，按一下 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-160">In the Contoso-FabrikamCA Properties dialog box, on the **Policy Module** tab, click **Properties**.</span></span>  
  
4.  <span data-ttu-id="a9ac0-161">在 屬性 對話方塊中，選取**遵循憑證範本中的設定**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-161">In the Properties dialog box, select **Follow the settings in the certificate template**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="a9ac0-162">按一下**確定**以關閉 [Contoso-fabrikamca] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-162">Click **OK** to close the Contoso-FabrikamCA dialog box.</span></span>  
  
6.  <span data-ttu-id="a9ac0-163">關閉 [憑證授權單位] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-163">Close the Certification Authority dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a9ac0-164">啟用自動憑證核發之後，憑證服務便會自動化憑證核發程序。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-164">By enabling automatic certificate issuing, Certificate Services automates the certificate issuing procedure.</span></span> <span data-ttu-id="a9ac0-165">您必須重新啟動憑證服務，使這個變更生效。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-165">You will have to restart Certificate Services to apply this change.</span></span>  
    >   
    >  <span data-ttu-id="a9ac0-166">您可能需要將根憑證 Contoso-FabrikamCA.cer 安裝在 Current User\Trusted Root Certification authorities 中。</span><span class="sxs-lookup"><span data-stu-id="a9ac0-166">You may need to install the Root Certificate Contoso-FabrikamCA.cer in the Current User\Trusted Root Certification authorities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9ac0-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9ac0-167">See Also</span></span>  
 [<span data-ttu-id="a9ac0-168">步驟 2： 建立公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="a9ac0-168">Step 2: Creating Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)