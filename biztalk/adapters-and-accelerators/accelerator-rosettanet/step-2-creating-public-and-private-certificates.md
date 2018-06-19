---
title: 步驟 2： 建立公開憑證與私用憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating certificates
- public certificates
- certificates, public certificates
- creating, certificates
- private certificates
ms.assetid: 0a925d89-03d9-41fe-907b-85a6ae42362a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c26765b19c868dbb78d3924069b60161827312c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25967596"
---
# <a name="step-2-creating-public-and-private-certificates"></a><span data-ttu-id="b1126-102">步驟 2： 建立公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="b1126-102">Step 2: Creating Public and Private Certificates</span></span>
<span data-ttu-id="b1126-103">在此步驟中，您可以使用憑證授權單位中建立[步驟 1： 建立憑證授權單位 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)以產生 Contoso 及 Fabrikam 組織使用的公用和私用憑證。</span><span class="sxs-lookup"><span data-stu-id="b1126-103">In this step, you use the Certification Authority created in [Step 1: Creating a Certification Authority &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md) to generate the public and private certificates that the Contoso and Fabrikam organizations use.</span></span>  
  
### <a name="to-generate-the-contoso-and-fabrikam-encryption-certificates"></a><span data-ttu-id="b1126-104">產生 Contoso 及 Fabrikam 加密憑證</span><span class="sxs-lookup"><span data-stu-id="b1126-104">To generate the Contoso and Fabrikam encryption certificates</span></span>  
  
1.  <span data-ttu-id="b1126-105">在當做憑證授權單位使用的電腦上，於 Internet Explorer 中找出並且開啟 http://<contoso_computername>/certsrv。</span><span class="sxs-lookup"><span data-stu-id="b1126-105">On the computer you used as the Certification Authority, in Internet Explorer, locate and open http://<contoso_computername>/certsrv.</span></span>  
  
2.  <span data-ttu-id="b1126-106">在**歡迎**頁面上，按一下**要求憑證**。</span><span class="sxs-lookup"><span data-stu-id="b1126-106">On the **Welcome** page, click **Request a certificate**.</span></span>  
  
3.  <span data-ttu-id="b1126-107">在**要求憑證**頁面上，按一下**進階的憑證要求**。</span><span class="sxs-lookup"><span data-stu-id="b1126-107">On the **Request a Certificate** page, click **advanced certificate request**.</span></span>  
  
4.  <span data-ttu-id="b1126-108">在**進階憑證要求**頁面上，按一下**建立並提交一個要求向這個 CA**。</span><span class="sxs-lookup"><span data-stu-id="b1126-108">On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.</span></span>  
  
5.  <span data-ttu-id="b1126-109">在**進階憑證要求**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b1126-109">On the **Advanced Certificate Request** page, do the following:</span></span>  
  
    |<span data-ttu-id="b1126-110">使用</span><span class="sxs-lookup"><span data-stu-id="b1126-110">Use this</span></span>|<span data-ttu-id="b1126-111">動作</span><span class="sxs-lookup"><span data-stu-id="b1126-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b1126-112">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b1126-112">**Name**</span></span>|<span data-ttu-id="b1126-113">型別**Fabrikam Encryption**。</span><span class="sxs-lookup"><span data-stu-id="b1126-113">Type **Fabrikam Encryption**.</span></span>|  
    |<span data-ttu-id="b1126-114">**電子郵件**</span><span class="sxs-lookup"><span data-stu-id="b1126-114">**E-Mail**</span></span>|<span data-ttu-id="b1126-115">型別 **jdoe@fabrikam.com** 。</span><span class="sxs-lookup"><span data-stu-id="b1126-115">Type **jdoe@fabrikam.com**.</span></span>|  
    |<span data-ttu-id="b1126-116">**公司**</span><span class="sxs-lookup"><span data-stu-id="b1126-116">**Company**</span></span>|<span data-ttu-id="b1126-117">型別**Fabrikam**。</span><span class="sxs-lookup"><span data-stu-id="b1126-117">Type **Fabrikam**.</span></span>|  
    |<span data-ttu-id="b1126-118">**部門**</span><span class="sxs-lookup"><span data-stu-id="b1126-118">**Department**</span></span>|<span data-ttu-id="b1126-119">型別**測試**。</span><span class="sxs-lookup"><span data-stu-id="b1126-119">Type **Test**.</span></span>|  
    |<span data-ttu-id="b1126-120">**City**</span><span class="sxs-lookup"><span data-stu-id="b1126-120">**City**</span></span>|<span data-ttu-id="b1126-121">型別**測試**。</span><span class="sxs-lookup"><span data-stu-id="b1126-121">Type **Test**.</span></span>|  
    |<span data-ttu-id="b1126-122">**State**</span><span class="sxs-lookup"><span data-stu-id="b1126-122">**State**</span></span>|<span data-ttu-id="b1126-123">型別**測試**。</span><span class="sxs-lookup"><span data-stu-id="b1126-123">Type **Test**.</span></span>|  
    |<span data-ttu-id="b1126-124">**國家/地區**</span><span class="sxs-lookup"><span data-stu-id="b1126-124">**Country/Region**</span></span>|<span data-ttu-id="b1126-125">型別**美國**。</span><span class="sxs-lookup"><span data-stu-id="b1126-125">Type **US**.</span></span>|  
    |<span data-ttu-id="b1126-126">**需要的憑證類型**</span><span class="sxs-lookup"><span data-stu-id="b1126-126">**Type of Certificate Needed**</span></span>|<span data-ttu-id="b1126-127">選取**電子郵件保護憑證**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b1126-127">Select **E-Mail Protection Certificate** from the drop down list.</span></span>|  
    |<span data-ttu-id="b1126-128">**金鑰使用方法**</span><span class="sxs-lookup"><span data-stu-id="b1126-128">**Key Usage**</span></span>|<span data-ttu-id="b1126-129">選取**Exchange**選項。</span><span class="sxs-lookup"><span data-stu-id="b1126-129">Select the **Exchange** option.</span></span>|  
    |<span data-ttu-id="b1126-130">**其他金鑰選項**</span><span class="sxs-lookup"><span data-stu-id="b1126-130">**Additional Key Options**</span></span>|<span data-ttu-id="b1126-131">核取下列選項：</span><span class="sxs-lookup"><span data-stu-id="b1126-131">Place a check in the following options:</span></span><br /><br /> <span data-ttu-id="b1126-132">-   **將金鑰標示成可匯出**</span><span class="sxs-lookup"><span data-stu-id="b1126-132">-   **Mark keys as exportable**</span></span><br /><span data-ttu-id="b1126-133">-   **將憑證儲存在本機電腦憑證存放區**</span><span class="sxs-lookup"><span data-stu-id="b1126-133">-   **Store certificate in the local computer certificate store**</span></span>|  
    |<span data-ttu-id="b1126-134">**易記名稱**</span><span class="sxs-lookup"><span data-stu-id="b1126-134">**Friendly Name**</span></span>|<span data-ttu-id="b1126-135">型別**Fabrikam Encryption**。</span><span class="sxs-lookup"><span data-stu-id="b1126-135">Type **Fabrikam Encryption**.</span></span>|  
  
6.  <span data-ttu-id="b1126-136">按一下**送出**，然後按一下 [**是**中**Web 存取確認**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b1126-136">Click **Submit**, and then click **Yes** in **Web Access Confirmation** dialog box.</span></span>  
  
7.  <span data-ttu-id="b1126-137">在**憑證核發**頁面上，按一下**安裝這個憑證**。</span><span class="sxs-lookup"><span data-stu-id="b1126-137">On the **Certificate Issued** page, click **Install this certificate**.</span></span>  
  
8.  <span data-ttu-id="b1126-138">重複步驟 1-7 中的資訊變更**名稱**方塊中**識別資訊**區段和**易記名稱**方塊**Contoso加密**。</span><span class="sxs-lookup"><span data-stu-id="b1126-138">Repeat steps 1-7, changing the information in the **Name** box in the **Identifying Information** section and the **Friendly Name** box to **Contoso Encryption**.</span></span>  
  
### <a name="to-generate-the-contoso-and-fabrikam-signing-certificates"></a><span data-ttu-id="b1126-139">產生 Contoso 及 Fabrikam 簽章憑證</span><span class="sxs-lookup"><span data-stu-id="b1126-139">To generate the Contoso and Fabrikam Signing Certificates</span></span>  
  
1.  <span data-ttu-id="b1126-140">在 Internet Explorer 中，尋找及開啟 http://<contoso_computername>/certsrv。</span><span class="sxs-lookup"><span data-stu-id="b1126-140">In Internet Explorer, locate and open http://<contoso_computername>/certsrv.</span></span>  
  
2.  <span data-ttu-id="b1126-141">在**歡迎**頁面上，按一下**要求憑證**。</span><span class="sxs-lookup"><span data-stu-id="b1126-141">On the **Welcome** page, click **Request a certificate**.</span></span>  
  
3.  <span data-ttu-id="b1126-142">在**要求憑證**頁面上，按一下**進階的憑證要求**。</span><span class="sxs-lookup"><span data-stu-id="b1126-142">On the **Request a Certificate** page, click **advanced certificate request**.</span></span>  
  
4.  <span data-ttu-id="b1126-143">在**進階憑證要求**頁面上，按一下**建立並提交一個要求向這個 CA**。</span><span class="sxs-lookup"><span data-stu-id="b1126-143">On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.</span></span>  
  
5.  <span data-ttu-id="b1126-144">在**進階憑證要求**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="b1126-144">On the **Advanced Certificate Request** page, do the following:</span></span>  
  
    |<span data-ttu-id="b1126-145">使用</span><span class="sxs-lookup"><span data-stu-id="b1126-145">Use this</span></span>|<span data-ttu-id="b1126-146">動作</span><span class="sxs-lookup"><span data-stu-id="b1126-146">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b1126-147">**名稱**</span><span class="sxs-lookup"><span data-stu-id="b1126-147">**Name**</span></span>|<span data-ttu-id="b1126-148">型別**Fabrikam Signature**。</span><span class="sxs-lookup"><span data-stu-id="b1126-148">Type **Fabrikam Signature**.</span></span>|  
    |<span data-ttu-id="b1126-149">**電子郵件**</span><span class="sxs-lookup"><span data-stu-id="b1126-149">**E-Mail**</span></span>|<span data-ttu-id="b1126-150">型別 **jdoe@fabrikam.com** 。</span><span class="sxs-lookup"><span data-stu-id="b1126-150">Type **jdoe@fabrikam.com**.</span></span>|  
    |<span data-ttu-id="b1126-151">**公司**</span><span class="sxs-lookup"><span data-stu-id="b1126-151">**Company**</span></span>|<span data-ttu-id="b1126-152">型別**Fabrikam**。</span><span class="sxs-lookup"><span data-stu-id="b1126-152">Type **Fabrikam**.</span></span>|  
    |<span data-ttu-id="b1126-153">**部門**</span><span class="sxs-lookup"><span data-stu-id="b1126-153">**Department**</span></span>|<span data-ttu-id="b1126-154">型別**測試**。</span><span class="sxs-lookup"><span data-stu-id="b1126-154">Type **Test**.</span></span>|  
    |<span data-ttu-id="b1126-155">**City**</span><span class="sxs-lookup"><span data-stu-id="b1126-155">**City**</span></span>|<span data-ttu-id="b1126-156">型別**測試**。</span><span class="sxs-lookup"><span data-stu-id="b1126-156">Type **Test**.</span></span>|  
    |<span data-ttu-id="b1126-157">**State**</span><span class="sxs-lookup"><span data-stu-id="b1126-157">**State**</span></span>|<span data-ttu-id="b1126-158">型別**測試**。</span><span class="sxs-lookup"><span data-stu-id="b1126-158">Type **Test**.</span></span>|  
    |<span data-ttu-id="b1126-159">**國家/地區**</span><span class="sxs-lookup"><span data-stu-id="b1126-159">**Country/Region**</span></span>|<span data-ttu-id="b1126-160">型別**美國**。</span><span class="sxs-lookup"><span data-stu-id="b1126-160">Type **US**.</span></span>|  
    |<span data-ttu-id="b1126-161">**需要的憑證類型**</span><span class="sxs-lookup"><span data-stu-id="b1126-161">**Type of Certificate Needed**</span></span>|<span data-ttu-id="b1126-162">選取**電子郵件保護憑證**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="b1126-162">Select **E-Mail Protection Certificate**.from the drop down list.</span></span>|  
    |<span data-ttu-id="b1126-163">**金鑰使用方法**</span><span class="sxs-lookup"><span data-stu-id="b1126-163">**Key Usage**</span></span>|<span data-ttu-id="b1126-164">選取**簽章**選項。</span><span class="sxs-lookup"><span data-stu-id="b1126-164">Select the **Signature** option.</span></span>|  
    |<span data-ttu-id="b1126-165">**其他金鑰選項**</span><span class="sxs-lookup"><span data-stu-id="b1126-165">**Additional Key Options**</span></span>|<span data-ttu-id="b1126-166">核取下列選項：</span><span class="sxs-lookup"><span data-stu-id="b1126-166">Place a check in the following options:</span></span><br /><br /> <span data-ttu-id="b1126-167">-   **將金鑰標示成可匯出**</span><span class="sxs-lookup"><span data-stu-id="b1126-167">-   **Mark keys as exportable**</span></span><br /><span data-ttu-id="b1126-168">-   **將憑證儲存在本機電腦憑證存放區**</span><span class="sxs-lookup"><span data-stu-id="b1126-168">-   **Store certificate in the local computer certificate store**</span></span>|  
    |<span data-ttu-id="b1126-169">**易記名稱**</span><span class="sxs-lookup"><span data-stu-id="b1126-169">**Friendly Name**</span></span>|<span data-ttu-id="b1126-170">型別**Fabrikam Signature**。</span><span class="sxs-lookup"><span data-stu-id="b1126-170">Type **Fabrikam Signature**.</span></span>|  
  
6.  <span data-ttu-id="b1126-171">按一下**送出**，然後按一下 **是**當詢問要求憑證。</span><span class="sxs-lookup"><span data-stu-id="b1126-171">Click **Submit**, and then click **Yes** when asked to request the certificate.</span></span>  
  
7.  <span data-ttu-id="b1126-172">在**憑證核發**頁面上，按一下**安裝這個憑證**。</span><span class="sxs-lookup"><span data-stu-id="b1126-172">On the **Certificate Issued** page, click **Install this certificate**.</span></span>  
  
8.  <span data-ttu-id="b1126-173">重複步驟 1-7 中的資訊變更**名稱**方塊中**識別資訊**區段和**易記名稱**方塊**Contoso簽章**。</span><span class="sxs-lookup"><span data-stu-id="b1126-173">Repeat steps 1-7, changing the information in the **Name** box in the **Identifying Information** section and the **Friendly Name** box to **Contoso Signature**.</span></span>  
  
### <a name="to-generate-private-certificates-for-the-encryption-and-signature-certificates"></a><span data-ttu-id="b1126-174">為加密憑證及簽章憑證產生私用憑證</span><span class="sxs-lookup"><span data-stu-id="b1126-174">To generate private certificates for the Encryption and Signature certificates</span></span>  
  
1.  <span data-ttu-id="b1126-175">按一下**啟動**，按一下 **執行**，型別**MMC**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b1126-175">Click **Start**, click **Run**, type **MMC**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b1126-176">在 Console1 視窗上**檔案**功能表上，按一下 **新增/移除嵌入式管理單元**。</span><span class="sxs-lookup"><span data-stu-id="b1126-176">In the Console1 window, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="b1126-177">在 新增/移除嵌入式管理單元 對話方塊中，在**獨立**索引標籤上，按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="b1126-177">In the Add/Remove Snap-in dialog box, on the **Standalone** tab, click **Add**.</span></span>  
  
4.  <span data-ttu-id="b1126-178">在 [新增獨立嵌入式管理單元] 對話方塊中，選取**憑證**嵌入式管理單元從**可用的獨立嵌入式管理單元**清單，然後再按**新增**。</span><span class="sxs-lookup"><span data-stu-id="b1126-178">In the Add Standalone Snap-in dialog box, select the **Certificates** snap-in from the **Available Standalone Snap-ins** list, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="b1126-179">在 憑證嵌入式管理單元對話方塊中，選取**我的使用者帳戶**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-179">In the Certificates snap-in dialog box, select **My user account**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="b1126-180">在 選取電腦 對話方塊中，按一下 **完成**。</span><span class="sxs-lookup"><span data-stu-id="b1126-180">In the Select Computer dialog box, click **Finish**.</span></span>  
  
7.  <span data-ttu-id="b1126-181">在 [新增獨立嵌入式管理單元] 對話方塊中，按一下**關閉**。</span><span class="sxs-lookup"><span data-stu-id="b1126-181">In the Add Standalone Snap-in dialog box, click **Close**.</span></span>  
  
8.  <span data-ttu-id="b1126-182">在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="b1126-182">In the Add/Remove Snap-in dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="b1126-183">在 主控台 1 視窗中，展開**憑證 （本機電腦）**，依序展開**個人**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="b1126-183">In the Console1 window, expand **Certificates (Local Computer)**, expand **Personal**, and then click **Certificates**.</span></span>  
  
10. <span data-ttu-id="b1126-184">在右窗格中，以滑鼠右鍵按一下**Fabrikam Encryption**憑證，指向**所有工作**，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="b1126-184">In the right pane, right-click the **Fabrikam Encryption** certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
11. <span data-ttu-id="b1126-185">在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-185">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
12. <span data-ttu-id="b1126-186">在**匯出私密金鑰**頁面上，選取**是，匯出私密金鑰**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-186">On the **Export Private Key** page, select **Yes, export the private key**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="b1126-187">在**匯出檔案格式**頁面上，請確定**個人資訊交換**是唯一選取的選項，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-187">On the **Export File Format** page, make sure that **Personal Information Exchange** is the only option selected, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="b1126-188">在**密碼**頁面上，於**密碼**和**確認密碼**方塊中，輸入**mysecret**，然後按一下 [**下一步]**.</span><span class="sxs-lookup"><span data-stu-id="b1126-188">On the **Password** page, in the **Password** and **Confirm Password** boxes, type **mysecret**, and then click **Next**.</span></span>  
  
15. <span data-ttu-id="b1126-189">在**要匯出的檔案**頁面上，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="b1126-189">On the **File To Export** page, click **Browse**.</span></span>  
  
16. <span data-ttu-id="b1126-190">在**存**對話方塊中，使用的檔案路徑的憑證儲存*\<磁碟機\>*: \Certs\Fabrikam Private Encryption.pfx。</span><span class="sxs-lookup"><span data-stu-id="b1126-190">In the **Save As** dialog box, save the certificate using the file path *\<drive\>*:\Certs\Fabrikam Private Encryption.pfx.</span></span>  
  
17. <span data-ttu-id="b1126-191">在**要匯出的檔案**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-191">On the **File to Export** page, click **Next**.</span></span>  
  
18. <span data-ttu-id="b1126-192">在**完成憑證匯出精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="b1126-192">On the **Completing the Certificate Export Wizard** page, click **Finish**.</span></span>  
  
19. <span data-ttu-id="b1126-193">在 憑證匯出精靈 快顯視窗表示匯出成功，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b1126-193">In the Certificate Export Wizard popup indicating a successful export, click **OK**.</span></span>  
  
20. <span data-ttu-id="b1126-194">針對 Fabrikam Signature 憑證重複執行步驟 10-19，並另存為 Fabrikam Private Signature.pfx 檔名。</span><span class="sxs-lookup"><span data-stu-id="b1126-194">Repeat steps 10-19 for the Fabrikam Signature certificate using the file name Fabrikam Private Signature.pfx.</span></span>  
  
21. <span data-ttu-id="b1126-195">針對 Contoso Signature 憑證和 Contoso Encryption 憑證重複執行步驟 10-19，並分別另存為 Contoso Private Signature.pfx 及 Contoso Private Encryption.pfx。</span><span class="sxs-lookup"><span data-stu-id="b1126-195">Repeat steps 10-19 for the Contoso Signature and Contoso Encryption certificates using the file names Contoso Private Signature.pfx and Contoso Private Encryption.pfx, respectively.</span></span>  
  
### <a name="to-generate-public-certificates-for-the-encryption-and-signature-certificates"></a><span data-ttu-id="b1126-196">為加密憑證及簽章憑證產生公開憑證</span><span class="sxs-lookup"><span data-stu-id="b1126-196">To generate public certificates for the Encryption and Signature certificates</span></span>  
  
1.  <span data-ttu-id="b1126-197">在 主控台 1 視窗中，展開**憑證 – 目前使用者**，依序展開**個人**，然後按一下 **憑證**。</span><span class="sxs-lookup"><span data-stu-id="b1126-197">In the Console1 window, expand **Certificates – Current User**, expand **Personal**, and then click **Certificates**.</span></span>  
  
2.  <span data-ttu-id="b1126-198">以滑鼠右鍵按一下**Fabrikam Encryption**憑證，指向**所有工作**，然後按一下 **匯出**。</span><span class="sxs-lookup"><span data-stu-id="b1126-198">Right-click the **Fabrikam Encryption** certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
3.  <span data-ttu-id="b1126-199">在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-199">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="b1126-200">在**匯出私密金鑰**頁面上，選取**否，不要匯出私密金鑰**，然後按一下 **下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-200">On the **Export Private Key** page, select **No, do not export the private key**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="b1126-201">在**匯出檔案格式**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-201">On the **Export File Format** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="b1126-202">在**要匯出的檔案**頁面上，按一下**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="b1126-202">On the **File To Export** page, click **Browse**.</span></span>  
  
7.  <span data-ttu-id="b1126-203">在 另存新檔 對話方塊中，輸入**\<磁碟機\>: \Certs**如**存**， **Fabrikam Public Encryption.cer**為**檔案名稱**，和 **\*.cer**如**存檔類型**，然後按一下 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="b1126-203">In the Save As dialog box, enter **\<drive\>:\Certs** for **Save in**, **Fabrikam Public Encryption.cer** as **File name**, and **\*.cer** for **Save as type**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="b1126-204">在**要匯出的檔案**頁面上，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="b1126-204">On the **File to Export** page, click **Next**.</span></span>  
  
9. <span data-ttu-id="b1126-205">在**完成憑證匯出精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="b1126-205">On the **Completing the Certificate Export Wizard** page, click **Finish**.</span></span>  
  
10. <span data-ttu-id="b1126-206">在 憑證匯出精靈 快顯視窗表示匯出成功，按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="b1126-206">In the Certificate Export Wizard popup indicating a successful export, click **OK**.</span></span>  
  
11. <span data-ttu-id="b1126-207">針對 Fabrikam 簽章憑證重複執行步驟 1-9，並另存為 Fabrikam Public Signature.cer 檔名。</span><span class="sxs-lookup"><span data-stu-id="b1126-207">Repeat steps 1-9 for the Fabrikam Signature certificate using the file name Fabrikam Public Signature.cer.</span></span>  
  
12. <span data-ttu-id="b1126-208">針對 Contoso Signature 憑證和 Contoso Encryption 憑證重複執行步驟 1-9，並分別另存為 Contoso Public Signature.cer 及 Contoso Public Encryption.cer。</span><span class="sxs-lookup"><span data-stu-id="b1126-208">Repeat steps 1-9 for the Contoso Signature and Contoso Encryption certificates using the file names Contoso Public Signature.cer and Contoso Public Encryption.cer, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1126-209">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1126-209">See Also</span></span>  
 [<span data-ttu-id="b1126-210">步驟 3：匯入公開憑證與私用憑證</span><span class="sxs-lookup"><span data-stu-id="b1126-210">Step 3: Importing Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)