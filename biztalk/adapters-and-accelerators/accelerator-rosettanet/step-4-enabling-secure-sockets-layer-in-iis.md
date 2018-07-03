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
# <a name="step-4-enabling-secure-sockets-layer-in-iis"></a>步驟 4： 啟用安全通訊端在 IIS 中的圖層
安全通訊端層 (Secure Sockets Layer，SSL) 是為了保護用戶端及伺服器之間通訊管道而設計的通訊協定。 透過啟用 Microsoft® Internet Information Services (IIS) 7.5/7.0 中的 SSL，Contoso 和 Fabrikam 組織即可使用驗證及加密，針對所有資料傳輸進行通訊。 在此步驟中，您將學習如何啟用 IIS 7.5/7.0 中的 SSL。  
  
> [!NOTE]
>  您必須在 Contoso 和 Fabrikam 電腦上執行此步驟。  
  
### <a name="to-prepare-a-new-server-certificate"></a>準備新的伺服器憑證  
  
1. 按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2. 在 Internet Information Services 左側窗格中，依序展開**\<** <em>computer_name</em> **\>** (*本機電腦*)，依序展開**網站**，以滑鼠右鍵按一下**Default Web Site**，然後按一下**屬性**。  
  
3. 在 預設網站 對話方塊中上,**目錄安全**索引標籤上，按一下 **伺服器憑證**來啟動**IIS 憑證精靈**。  
  
4. 在 [**歡迎使用 Web 伺服器憑證精靈**頁面上，按一下**下一步]**。  
  
5. 在 [**伺服器憑證**頁面上，選取**建立新的憑證**，然後按一下**下一步]**。  
  
6. 在 [**延遲或立即要求**頁面上，按一下**下一步]**。  
  
7. 在 [**名稱和安全性設定**頁面上，按一下**下一步]**，保留預設設定。  
  
8. 在 [**組織資訊**頁面上，於**組織**方塊中，輸入**Contoso**如果 Contoso 電腦上的或**Fabrikam**如果在Fabrikam 電腦，請在**組織單位**方塊中，輸入**測試**，然後按一下**下一步]**。  
  
9. 在上**您站台的一般名稱**頁面上，於**一般名稱**方塊中，輸入您的電腦名稱，然後按一下**下一步**。  
  
10. 在上**地理資訊**頁面上，於**縣/市**方塊中，輸入您的縣/市，**城市/位置**方塊中輸入您的城市位置，然後再按一下**下一步**。  
  
11. 在上**憑證要求檔案名稱**頁面上，於**檔案名稱**方塊中，保留預設值**C:\certreq.txt**，然後按一下**下一步**。  
  
12. 在 [**要求的檔案摘要**頁面上，按一下**下一步]**。  
  
13. 在上**完成 Web 伺服器憑證精靈**頁面上，按一下**完成**以關閉**IIS 憑證精靈**。  
  
### <a name="to-generate-a-new-server-certificate"></a>產生新的伺服器憑證  
  
1.  在 Internet Explorer 中，尋找及開啟 http://\<*contoso_machine*\>/CertSrv。  
  
    > [!NOTE]
    >  在步驟 1 中，開啟 http://\<*contoso_machine*\>/CertSrv Contoso 或 Fabrikam 電腦上的。  
  
2.  在  **Microsoft 憑證服務歡迎使用精靈**頁面上，按一下**要求憑證。**  
  
3.  在 **要求的憑證**頁面上，按一下**進階的憑證要求**。  
  
4.  在 **進階憑證要求**頁面上，按一下**使用 base-64 編碼的 CMC 或 PKCS #10 檔案，來提交憑證要求，或使用 base-64 編碼的 PKCS #7 檔案提交更新要求**。  
  
5.  在 **提交憑證要求或更新要求**頁面上，按一下**瀏覽要插入的檔案**。  
  
    > [!NOTE]
    >  如果按一下連結時，您會收到安全性錯誤，[記事本] 或其他文字編輯器開啟 C:\certreq.txt 檔案，複製檔案的內容並貼上該資訊**已儲存的要求**方塊，然後再按一下**提交**。 接著，您可以前往步驟 10。  
  
6.  按一下 [**瀏覽**來開啟**選擇檔案**] 對話方塊。  
  
7.  在 **選擇檔案**對話方塊方塊中，找出*\<磁碟機\>*: \ 資料夾中，選取 certreq.txt 檔案，然後按一下**開啟**。  
  
8.  在 **提交憑證要求或更新要求**頁面上，按一下**讀取**。  
  
9. 在 **提交憑證要求或更新要求**頁面上，按一下**送出**來產生新的憑證。  
  
10. 在上**憑證核發**頁面上，按一下**下載的憑證**。  
  
11. 在 [**檔案下載**] 對話方塊中，按一下**儲存**。  
  
12. 在 **另存新檔**對話方塊中，將憑證儲存到\<磁碟機\>: \Certs\SSLCert.cer，，然後按一下**儲存**。  
  
13. 按一下 [**關閉**以關閉**下載完整**] 對話方塊。  
  
### <a name="to-prepare-a-new-server-certificate-for-iis"></a>若要準備 IIS 的新伺服器憑證  
  
1.  按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2.  在 Internet Information Services 左側窗格中，按一下 < 電腦名稱 > （本機電腦） 中，按兩下 **伺服器憑證**右窗格中。 選取 **建立憑證要求**從 動作 窗格中。  
  
3.  在 [辨別名稱屬性] 對話方塊中輸入的一般名稱中的電腦名稱： 文字方塊中，組織中： 方塊中，輸入**Contoso**如果 Contoso 電腦上的或**Fabrikam**如果在 Fabrikam組織單位中的電腦： 方塊中，輸入測試，請在 [城市/位置] 方塊中，在 [縣/市] 方塊中輸入您的城市位置，，輸入您的縣/市、 國家 （地區） 下拉式清單，選取您的國家/地區，然後按一下**下一步**.  
  
4.  在 密碼編譯服務提供者內容 對話方塊中，按一下**下一步**。  
  
5.  在 [檔案名稱] 對話方塊中，指定 C:\certreq.txt，在文字方塊中，按一下**完成**。  
  
### <a name="to-generate-a-new-server-certificate-for-iis"></a>若要產生 IIS 的新伺服器憑證  
  
1.  在 Internet Explorer 中，找出並開啟 http://<contoso_machine>/CertSrv。  
  
    > [!NOTE]
    >  在步驟 1 中，開啟 Contoso 或 Fabrikam 電腦上的 http://<contoso_machine>/CertSrv。  
  
2.  在 Microsoft 憑證服務歡迎使用精靈的頁面上，按一下**要求憑證**。  
  
3.  在 [要求憑證] 頁面上，按一下**進階憑證要求**。  
  
4.  在 進階憑證要求 頁面中，按一下 **提交憑證要求**藉由使用 base-64 編碼的 CMC 或 PKCS #10 檔案，或使用 base-64 編碼的 PKCS #7 檔案提交更新要求。  
  
5.  在 記事本 或其他文字編輯器開啟 C:\certreq.txt 檔案、 檔案的內容複製和貼上該資訊**已儲存的要求**方塊在 提交憑證要求或更新要求的頁面上，，然後按一下  **提交**。  
  
6.  在 [憑證已發出] 頁面上按一下**下載憑證**。  
  
7.  在 [檔案下載] 對話方塊中，按一下**儲存**。  
  
8.  在 [另存新檔] 對話方塊中，將儲存的憑證\<磁碟機\>: \Certs\SSLCert.cer，，然後按一下**儲存**。  
  
### <a name="to-import-the-server-certificate-into-iis"></a>若要將伺服器憑證匯入 IIS  
  
1.  按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2.  在 Internet Information Services 左側窗格中，按一下 **（本機電腦）**，按兩下**伺服器憑證**右窗格中。 選取 **完成憑證要求**從 動作 窗格。  
  
3.  在指定的憑證授權單位回應對話方塊方塊中輸入**\<磁碟機\>: \Certs\SSLCert.cer**中**包含憑證授權單位回應的檔案名稱**文字方塊。 在 好記名稱文字方塊中輸入**ContosoSSLCert**。  
  
### <a name="to-enable-ssl-bindings-for-iis"></a>若要啟用 IIS 的 SSL 繫結  
  
1.  按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2.  在 Internet Information Services 左側窗格中，依序展開 **（本機電腦）**，展開**站台**，以滑鼠右鍵按一下**Default Web Site**，然後按一下 **編輯繫結**。  
  
3.  在站台繫結 對話方塊中按一下**新增**。 在 新增網站繫結 對話方塊中選取**https**從 類型 下拉式清單，選取**ContosoSSLCert** SSL 憑證下拉式清單中，按一下  **確定**，按一下 **關閉**.  
  
### <a name="to-import-the-server-certificate-into-iis"></a>若要將伺服器憑證匯入 IIS  
  
1. 按一下 **開始**，指向**系統管理工具**，然後按一下**Internet Information Services (IIS) 管理員**。  
  
2. 在 Internet Information Services 左側窗格中，依序展開**\<** <em>computer_name</em> \> (*本機電腦*)，依序展開**Web站台**，以滑鼠右鍵按一下**Default Web Site**，然後按一下**屬性**。  
  
3. 在預設的網站內容] 對話方塊中，在**目錄安全**索引標籤上，按一下 [**伺服器憑證**來啟動**IIS 憑證精靈**。  
  
4. 在 [**歡迎使用 Web 伺服器憑證精靈**頁面上，按一下**下一步]**。  
  
5. 在上**擱置的憑證要求**頁面上，選取**處理擱置要求及安裝憑證**，然後按一下**下一步**。  
  
6. 在上**處理擱置的要求**頁面上，於**路徑和檔名**方塊中，輸入**\<磁碟機\>: \Certs\SSLCert.cer** （或瀏覽至該檔案）然後按一下**下一步**。  
  
7. 在 [ **SSL 連接埠頁面**，按一下**下一步]**。  
  
8. 在 [**憑證摘要**頁面上，按一下**下一步]**。  
  
9. 在 **完成 Web 伺服器憑證精靈**頁面上，按一下**完成**。  
  
## <a name="see-also"></a>另請參閱  
 [建立與設定 Contoso 解決方案](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)