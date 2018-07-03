---
title: 步驟 4： 啟用安全通訊端在 IIS 中的圖層 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Secure Socket Layers
- IIS
- double action tutorial, enabling SSL in IIS
- SSL
ms.assetid: 96109294-595a-46ac-974e-33123df79ed5
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be53660b5632450d8fa8cb38480c9b728d460bad
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009159"
---
# <a name="step-4-enabling-secure-sockets-layer-in-iis"></a><span data-ttu-id="bb4d6-102">步驟 4： 啟用安全通訊端在 IIS 中的圖層</span><span class="sxs-lookup"><span data-stu-id="bb4d6-102">Step 4: Enabling Secure Sockets Layer in IIS</span></span>
<span data-ttu-id="bb4d6-103">安全通訊端層 (Secure Sockets Layer，SSL) 是為了保護用戶端及伺服器之間通訊管道而設計的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-103">Secure Sockets Layer (SSL) is a protocol designed to secure the communication channel between a client and a server.</span></span> <span data-ttu-id="bb4d6-104">透過啟用 Microsoft® Internet Information Services (IIS) 7.5/7.0 中的 SSL，Contoso 和 Fabrikam 組織即可使用驗證及加密，針對所有資料傳輸進行通訊。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-104">By enabling SSL in Microsoft® Internet Information Services (IIS) 7.5/7.0, the Contoso and Fabrikam organizations communicate using authentication and encryption for all data transfers.</span></span> <span data-ttu-id="bb4d6-105">在此步驟中，您將學習如何啟用 IIS 7.5/7.0 中的 SSL。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-105">In this step, you learn how to enable SSL in IIS 7.5/7.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bb4d6-106">您必須在 Contoso 和 Fabrikam 電腦上執行此步驟。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-106">You have to perform this step on both the Contoso and Fabrikam computers.</span></span>  
  
### <a name="to-prepare-a-new-server-certificate"></a><span data-ttu-id="bb4d6-107">準備新的伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="bb4d6-107">To prepare a new server certificate</span></span>  
  
1. <span data-ttu-id="bb4d6-108">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-108">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2. <span data-ttu-id="bb4d6-109">在 Internet Information Services 左側窗格中，依序展開**\<** <em>computer_name</em> **\>** (*本機電腦*)，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-109">In the Internet Information Services left pane, expand **\<**<em>computer_name</em>**\>** (*local computer*), expand **Web Sites**, right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="bb4d6-110">在 預設網站 對話方塊中上,**目錄安全**索引標籤上，按一下 **伺服器憑證**來啟動**IIS 憑證精靈**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-110">In the Default Web Sites dialog box, on the **Directory Security** tab, click **Server Certificate** to start the **IIS Certificate Wizard**.</span></span>  
  
4. <span data-ttu-id="bb4d6-111">在 [**歡迎使用 Web 伺服器憑證精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-111">On the **Welcome to the Web Server Certificate Wizard** page, click **Next**.</span></span>  
  
5. <span data-ttu-id="bb4d6-112">在 [**伺服器憑證**頁面上，選取**建立新的憑證**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-112">On the **Server Certificate** page, select **Create a new certificate**, and then click **Next**.</span></span>  
  
6. <span data-ttu-id="bb4d6-113">在 [**延遲或立即要求**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-113">On the **Delayed or immediate request** page, click **Next**.</span></span>  
  
7. <span data-ttu-id="bb4d6-114">在 [**名稱和安全性設定**頁面上，按一下**下一步]**，保留預設設定。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-114">On the **Name and Security Settings** page, click **Next**, keeping the defaults.</span></span>  
  
8. <span data-ttu-id="bb4d6-115">在 [**組織資訊**頁面上，於**組織**方塊中，輸入**Contoso**如果 Contoso 電腦上的或**Fabrikam**如果在Fabrikam 電腦，請在**組織單位**方塊中，輸入**測試**，然後按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-115">On the **Organization Information** page, in the **Organization** box, type **Contoso** if on the Contoso computer or **Fabrikam** if on the Fabrikam computer, in the **Organizational unit** box, type **Test**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="bb4d6-116">在上**您站台的一般名稱**頁面上，於**一般名稱**方塊中，輸入您的電腦名稱，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-116">On the **Your Site's Common Name** page, in the **Common name** box, type the name of your computer, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="bb4d6-117">在上**地理資訊**頁面上，於**縣/市**方塊中，輸入您的縣/市，**城市/位置**方塊中輸入您的城市位置，然後再按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-117">On the **Geographical Information** page, in the **State/province** box, type your state/province, in the **City/locality** box, type your city/locality, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="bb4d6-118">在上**憑證要求檔案名稱**頁面上，於**檔案名稱**方塊中，保留預設值**C:\certreq.txt**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-118">On the **Certificate Request File Name** page, in the **File name** box, leave the default **C:\certreq.txt**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="bb4d6-119">在 [**要求的檔案摘要**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-119">On the **Request File Summary** page, click **Next**.</span></span>  
  
13. <span data-ttu-id="bb4d6-120">在上**完成 Web 伺服器憑證精靈**頁面上，按一下**完成**以關閉**IIS 憑證精靈**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-120">On the **Completing the Web Server Certificate Wizard** page, click **Finish** to close the **IIS Certificate Wizard**.</span></span>  
  
### <a name="to-generate-a-new-server-certificate"></a><span data-ttu-id="bb4d6-121">產生新的伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="bb4d6-121">To generate a new server certificate</span></span>  
  
1.  <span data-ttu-id="bb4d6-122">在 Internet Explorer 中，尋找及開啟 http://\<*contoso_machine*\>/CertSrv。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-122">In Internet Explorer, locate and open http://\<*contoso_machine*\>/CertSrv.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb4d6-123">在步驟 1 中，開啟 http://\<*contoso_machine*\>/CertSrv Contoso 或 Fabrikam 電腦上的。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-123">In step 1, open http://\<*contoso_machine*\>/CertSrv on the Contoso or Fabrikam computer.</span></span>  
  
2.  <span data-ttu-id="bb4d6-124">在  **Microsoft 憑證服務歡迎使用精靈**頁面上，按一下**要求憑證。**</span><span class="sxs-lookup"><span data-stu-id="bb4d6-124">On the **Microsoft Certificate Services Wizard Welcome** page, click **Request a certificate.**</span></span>  
  
3.  <span data-ttu-id="bb4d6-125">在 **要求的憑證**頁面上，按一下**進階的憑證要求**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-125">On the **Request a Certificate** page, click **advanced certificate request**.</span></span>  
  
4.  <span data-ttu-id="bb4d6-126">在 **進階憑證要求**頁面上，按一下**使用 base-64 編碼的 CMC 或 PKCS #10 檔案，來提交憑證要求，或使用 base-64 編碼的 PKCS #7 檔案提交更新要求**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-126">On the **Advanced Certificate Request** page, click **Submit a certificate request by using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file**.</span></span>  
  
5.  <span data-ttu-id="bb4d6-127">在 **提交憑證要求或更新要求**頁面上，按一下**瀏覽要插入的檔案**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-127">On the **Submit a Certificate Request or Renewal Request** page, click **Browse for a file to insert**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb4d6-128">如果按一下連結時，您會收到安全性錯誤，[記事本] 或其他文字編輯器開啟 C:\certreq.txt 檔案，複製檔案的內容並貼上該資訊**已儲存的要求**方塊，然後再按一下**提交**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-128">If you receive a security error when clicking the link, open the file C:\certreq.txt in Notepad or another text editor, copy the contents of the file and paste that information in the **Saved Request** box, and then click **Submit**.</span></span> <span data-ttu-id="bb4d6-129">接著，您可以前往步驟 10。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-129">You can then go to step 10.</span></span>  
  
6.  <span data-ttu-id="bb4d6-130">按一下 [**瀏覽**來開啟**選擇檔案**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-130">Click **Browse** to open the **Choose File** dialog box.</span></span>  
  
7.  <span data-ttu-id="bb4d6-131">在 **選擇檔案**對話方塊方塊中，找出*\<磁碟機\>*: \ 資料夾中，選取 certreq.txt 檔案，然後按一下**開啟**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-131">In the **Choose File** dialog box, locate the *\<drive\>*:\ folder, select the certreq.txt file, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="bb4d6-132">在 **提交憑證要求或更新要求**頁面上，按一下**讀取**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-132">On the **Submit a Certificate Request or Renewal Request** page, click **Read**.</span></span>  
  
9. <span data-ttu-id="bb4d6-133">在 **提交憑證要求或更新要求**頁面上，按一下**送出**來產生新的憑證。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-133">On the **Submit a Certificate Request or Renewal Request** page, click **Submit** to generate the new certificate.</span></span>  
  
10. <span data-ttu-id="bb4d6-134">在上**憑證核發**頁面上，按一下**下載的憑證**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-134">On the **Certificate Issued** page, click **Download Certificate**.</span></span>  
  
11. <span data-ttu-id="bb4d6-135">在 [**檔案下載**] 對話方塊中，按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-135">In the **File Download** dialog box, click **Save**.</span></span>  
  
12. <span data-ttu-id="bb4d6-136">在 **另存新檔**對話方塊中，將憑證儲存到\<磁碟機\>: \Certs\SSLCert.cer，，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-136">In the **Save As** dialog box, save the certificate to \<drive\>:\Certs\SSLCert.cer, and then click **Save**.</span></span>  
  
13. <span data-ttu-id="bb4d6-137">按一下 [**關閉**以關閉**下載完整**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-137">Click **Close** to close the **Download Complete** dialog box.</span></span>  
  
### <a name="to-prepare-a-new-server-certificate-for-iis"></a><span data-ttu-id="bb4d6-138">若要準備 IIS 的新伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="bb4d6-138">To Prepare a new Server Certificate for IIS</span></span>  
  
1.  <span data-ttu-id="bb4d6-139">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-139">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="bb4d6-140">在 Internet Information Services 左側窗格中，按一下 < 電腦名稱 > （本機電腦） 中，按兩下 **伺服器憑證**右窗格中。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-140">In the Internet Information Services left pane, click <computer_name> (local computer), double click **Server Certificates** in the right pane.</span></span> <span data-ttu-id="bb4d6-141">選取 **建立憑證要求**從 動作 窗格中。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-141">Select **Create Certificate Request** from Actions pane.</span></span>  
  
3.  <span data-ttu-id="bb4d6-142">在 [辨別名稱屬性] 對話方塊中輸入的一般名稱中的電腦名稱： 文字方塊中，組織中： 方塊中，輸入**Contoso**如果 Contoso 電腦上的或**Fabrikam**如果在 Fabrikam組織單位中的電腦： 方塊中，輸入測試，請在 [城市/位置] 方塊中，在 [縣/市] 方塊中輸入您的城市位置，，輸入您的縣/市、 國家 （地區） 下拉式清單，選取您的國家/地區，然後按一下**下一步**.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-142">In Distinguished Name Properties dialog box type the name of the computer in the Common name: text box, in the Organization: box, type **Contoso** if on the Contoso computer or **Fabrikam** if on the Fabrikam computer, in the Organizational unit: box type Test, in the City/locality box, type your city/locality, in the State/province box, type your state/province, in the Country/region drop down, select your Country/region and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="bb4d6-143">在 密碼編譯服務提供者內容 對話方塊中，按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-143">In the Cryptographic Service Provider Properties dialog box, click **Next**.</span></span>  
  
5.  <span data-ttu-id="bb4d6-144">在 [檔案名稱] 對話方塊中，指定 C:\certreq.txt，在文字方塊中，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-144">In the File Name dialog box, specify C:\certreq.txt in the text box, click **Finish**.</span></span>  
  
### <a name="to-generate-a-new-server-certificate-for-iis"></a><span data-ttu-id="bb4d6-145">若要產生 IIS 的新伺服器憑證</span><span class="sxs-lookup"><span data-stu-id="bb4d6-145">To generate a new server certificate for IIS</span></span>  
  
1.  <span data-ttu-id="bb4d6-146">在 Internet Explorer 中，找出並開啟 http://<contoso_machine>/CertSrv。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-146">In Internet Explorer, locate and open http://<contoso_machine>/CertSrv.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb4d6-147">在步驟 1 中，開啟 Contoso 或 Fabrikam 電腦上的 http://<contoso_machine>/CertSrv。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-147">In step 1, open http://<contoso_machine>/CertSrv on the Contoso or Fabrikam computer.</span></span>  
  
2.  <span data-ttu-id="bb4d6-148">在 Microsoft 憑證服務歡迎使用精靈的頁面上，按一下**要求憑證**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-148">On the Microsoft Certificate Services Wizard Welcome page, click **Request a certificate**.</span></span>  
  
3.  <span data-ttu-id="bb4d6-149">在 [要求憑證] 頁面上，按一下**進階憑證要求**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-149">On the Request a Certificate page, click **Advanced Certificate Request**.</span></span>  
  
4.  <span data-ttu-id="bb4d6-150">在 進階憑證要求 頁面中，按一下 **提交憑證要求**藉由使用 base-64 編碼的 CMC 或 PKCS #10 檔案，或使用 base-64 編碼的 PKCS #7 檔案提交更新要求。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-150">On the Advanced Certificate Request page, click **Submit a certificate request** by using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file.</span></span>  
  
5.  <span data-ttu-id="bb4d6-151">在 記事本 或其他文字編輯器開啟 C:\certreq.txt 檔案、 檔案的內容複製和貼上該資訊**已儲存的要求**方塊在 提交憑證要求或更新要求的頁面上，，然後按一下  **提交**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-151">Open the file C:\certreq.txt in Notepad or another text editor, copy the contents of the file and paste that information in the **Saved Request** box on the Submit a Certificate Request or Renewal Request page, and then click **Submit**.</span></span>  
  
6.  <span data-ttu-id="bb4d6-152">在 [憑證已發出] 頁面上按一下**下載憑證**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-152">On the Certificate Issued page, click **Download Certificate**.</span></span>  
  
7.  <span data-ttu-id="bb4d6-153">在 [檔案下載] 對話方塊中，按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-153">In the File Download dialog box, click **Save**.</span></span>  
  
8.  <span data-ttu-id="bb4d6-154">在 [另存新檔] 對話方塊中，將儲存的憑證\<磁碟機\>: \Certs\SSLCert.cer，，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-154">In the Save As dialog box, save the certificate to \<drive\>:\Certs\SSLCert.cer, and then click **Save**.</span></span>  
  
### <a name="to-import-the-server-certificate-into-iis"></a><span data-ttu-id="bb4d6-155">若要將伺服器憑證匯入 IIS</span><span class="sxs-lookup"><span data-stu-id="bb4d6-155">To import the server certificate into IIS</span></span>  
  
1.  <span data-ttu-id="bb4d6-156">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-156">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="bb4d6-157">在 Internet Information Services 左側窗格中，按一下 **（本機電腦）**，按兩下**伺服器憑證**右窗格中。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-157">In the Internet Information Services left pane, click **(local computer)**, double click **Server Certificates** in the right pane.</span></span> <span data-ttu-id="bb4d6-158">選取 **完成憑證要求**從 動作 窗格。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-158">Select **Complete Certificate Request** from the Actions pane.</span></span>  
  
3.  <span data-ttu-id="bb4d6-159">在指定的憑證授權單位回應對話方塊方塊中輸入**\<磁碟機\>: \Certs\SSLCert.cer**中**包含憑證授權單位回應的檔案名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-159">In Specify Certificate Authority Response dialog box type **\<drive\>:\Certs\SSLCert.cer** in **File name containing the certification authority’s response** text box.</span></span> <span data-ttu-id="bb4d6-160">在 好記名稱文字方塊中輸入**ContosoSSLCert**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-160">In Friendly name text box type **ContosoSSLCert**.</span></span>  
  
### <a name="to-enable-ssl-bindings-for-iis"></a><span data-ttu-id="bb4d6-161">若要啟用 IIS 的 SSL 繫結</span><span class="sxs-lookup"><span data-stu-id="bb4d6-161">To enable SSL bindings for IIS</span></span>  
  
1.  <span data-ttu-id="bb4d6-162">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-162">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="bb4d6-163">在 Internet Information Services 左側窗格中，依序展開 **（本機電腦）**，展開**站台**，以滑鼠右鍵按一下**Default Web Site**，然後按一下 **編輯繫結**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-163">In the Internet Information Services left pane, expand **(local computer)**, expand **Sites**, right-click **Default Web Site**, and then click **Edit Bindings**.</span></span>  
  
3.  <span data-ttu-id="bb4d6-164">在站台繫結 對話方塊中按一下**新增**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-164">In Site Bindings dialog box click **Add**.</span></span> <span data-ttu-id="bb4d6-165">在 新增網站繫結 對話方塊中選取**https**從 類型 下拉式清單，選取**ContosoSSLCert** SSL 憑證下拉式清單中，按一下  **確定**，按一下 **關閉**.</span><span class="sxs-lookup"><span data-stu-id="bb4d6-165">In the Add Site Binding dialog box select **https** from Type drop down, select **ContosoSSLCert** from SSL certificate drop down, click **OK**, click **Close**.</span></span>  
  
### <a name="to-import-the-server-certificate-into-iis"></a><span data-ttu-id="bb4d6-166">若要將伺服器憑證匯入 IIS</span><span class="sxs-lookup"><span data-stu-id="bb4d6-166">To import the server certificate into IIS</span></span>  
  
1. <span data-ttu-id="bb4d6-167">按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-167">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2. <span data-ttu-id="bb4d6-168">在 Internet Information Services 左側窗格中，依序展開**\<** <em>computer_name</em> \> (*本機電腦*)，依序展開**Web站台**，以滑鼠右鍵按一下**Default Web Site**，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-168">In the Internet Information Services left pane, expand **\<**<em>computer_name</em>\> (*local computer*), expand **Web Sites**, right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
3. <span data-ttu-id="bb4d6-169">在預設的網站內容] 對話方塊中，在**目錄安全**索引標籤上，按一下 [**伺服器憑證**來啟動**IIS 憑證精靈**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-169">In the Default Web Site Properties dialog box, on the **Directory Security** tab, click **Server Certificate** to start the **IIS Certificate Wizard**.</span></span>  
  
4. <span data-ttu-id="bb4d6-170">在 [**歡迎使用 Web 伺服器憑證精靈**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-170">On the **Welcome to the Web Server Certificate Wizard** page, click **Next**.</span></span>  
  
5. <span data-ttu-id="bb4d6-171">在上**擱置的憑證要求**頁面上，選取**處理擱置要求及安裝憑證**，然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-171">On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.</span></span>  
  
6. <span data-ttu-id="bb4d6-172">在上**處理擱置的要求**頁面上，於**路徑和檔名**方塊中，輸入**\<磁碟機\>: \Certs\SSLCert.cer** （或瀏覽至該檔案）然後按一下**下一步**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-172">On the **Process a Pending Request** page, in the **Path and file name** box, type **\<drive\>:\Certs\SSLCert.cer** (or browse to that file) and then click **Next**.</span></span>  
  
7. <span data-ttu-id="bb4d6-173">在 [ **SSL 連接埠頁面**，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-173">On the **SSL Port page**, click **Next**.</span></span>  
  
8. <span data-ttu-id="bb4d6-174">在 [**憑證摘要**頁面上，按一下**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-174">On the **Certificate Summary** page, click **Next**.</span></span>  
  
9. <span data-ttu-id="bb4d6-175">在 **完成 Web 伺服器憑證精靈**頁面上，按一下**完成**。</span><span class="sxs-lookup"><span data-stu-id="bb4d6-175">On the **Completing the Web Server Certificate Wizard** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb4d6-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb4d6-176">See Also</span></span>  
 [<span data-ttu-id="bb4d6-177">建立與設定 Contoso 解決方案</span><span class="sxs-lookup"><span data-stu-id="bb4d6-177">Creating and Configuring the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)