---
title: 步驟 2： 建立公開憑證與私用憑證 |Microsoft Docs
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
ms.openlocfilehash: f31d1bb1dcc5a0e6f587797f41e97d16ca6606da
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007607"
---
# <a name="step-2-creating-public-and-private-certificates"></a>步驟 2： 建立公開憑證與私用憑證
在此步驟中，您可以使用在中建立的憑證授權單位[步驟 1： 建立憑證授權單位&#91;RN3&#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)以產生 Contoso 及 Fabrikam 組織使用的公用和私用憑證。  

### <a name="to-generate-the-contoso-and-fabrikam-encryption-certificates"></a>產生 Contoso 及 Fabrikam 加密憑證  

1. 在當做憑證授權單位使用的電腦上，於 Internet Explorer 中找出並且開啟 http://<contoso_computername>/certsrv。  

2. 在 **歡迎**頁面上，按一下**要求憑證**。  

3. 在 **要求的憑證**頁面上，按一下**進階的憑證要求**。  

4. 在 **進階憑證要求**頁面上，按一下**建立並提交一個要求，向這個 CA**。  

5. 在 **進階憑證要求**頁面上，執行下列動作：  


   |            使用            |                                                                         以進行此動作                                                                         |
   |--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **名稱**            |                                                               型別**Fabrikam Encryption**。                                                                |
   |           **電子郵件**           |                                                          型別<strong>jdoe@fabrikam.com</strong>。                                                          |
   |          **公司**           |                                                                     型別**Fabrikam**。                                                                     |
   |         **部門**         |                                                                       型別**測試**。                                                                       |
   |            **City**            |                                                                       型別**測試**。                                                                       |
   |           **State**            |                                                                       型別**測試**。                                                                       |
   |       **國家/地區**       |                                                                        型別**美國**。                                                                        |
   | **型別所需的憑證** |                                             選取 **電子郵件保護憑證**從下拉式清單。                                              |
   |         **金鑰使用方法**          |                                                              選取  **Exchange**選項。                                                               |
   |   **其他金鑰選項**   | 核取下列選項：<br /><br /> -   **將金鑰標示成可匯出**<br />-   **將憑證儲存在本機電腦憑證存放區** |
   |       **易記名稱**        |                                                               型別**Fabrikam Encryption**。                                                                |


6. 按一下 [**提交**，然後按一下**是**中**Web 存取確認**] 對話方塊。  

7. 在上**憑證核發**頁面上，按一下**安裝這個憑證**。  

8. 重複步驟 1-7，變更中的資訊**名稱**方塊中**識別資訊**區段並**易記名稱**方塊**Contoso加密**。  

### <a name="to-generate-the-contoso-and-fabrikam-signing-certificates"></a>產生 Contoso 及 Fabrikam 簽章憑證  

1. 在 Internet Explorer 中，找出並開啟 http://<contoso_computername>/certsrv。  

2. 在 **歡迎**頁面上，按一下**要求憑證**。  

3. 在 **要求的憑證**頁面上，按一下**進階的憑證要求**。  

4. 在 **進階憑證要求**頁面上，按一下**建立並提交一個要求，向這個 CA**。  

5. 在 **進階憑證要求**頁面上，執行下列動作：  


   |            使用            |                                                                         以進行此動作                                                                         |
   |--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |            **名稱**            |                                                                型別**Fabrikam Signature**。                                                                |
   |           **電子郵件**           |                                                          型別<strong>jdoe@fabrikam.com</strong>。                                                          |
   |          **公司**           |                                                                     型別**Fabrikam**。                                                                     |
   |         **部門**         |                                                                       型別**測試**。                                                                       |
   |            **City**            |                                                                       型別**測試**。                                                                       |
   |           **State**            |                                                                       型別**測試**。                                                                       |
   |       **國家/地區**       |                                                                        型別**美國**。                                                                        |
   | **型別所需的憑證** |                                             選取 **電子郵件保護憑證**從下拉式清單。                                              |
   |         **金鑰使用方法**          |                                                              選取 **簽章**選項。                                                              |
   |   **其他金鑰選項**   | 核取下列選項：<br /><br /> -   **將金鑰標示成可匯出**<br />-   **將憑證儲存在本機電腦憑證存放區** |
   |       **易記名稱**        |                                                                型別**Fabrikam Signature**。                                                                |


6. 按一下 **提交**，然後按一下**是**當詢問要求憑證。  

7. 在上**憑證核發**頁面上，按一下**安裝這個憑證**。  

8. 重複步驟 1-7，變更中的資訊**名稱**方塊中**識別資訊**區段並**易記名稱**方塊**Contoso簽章**。  

### <a name="to-generate-private-certificates-for-the-encryption-and-signature-certificates"></a>為加密憑證及簽章憑證產生私用憑證  

1.  按一下 **開始**，按一下**執行**，型別**MMC**，然後按一下 **確定**。  

2.  在 [Console1] 視窗中，在**檔案**功能表上，按一下**新增/移除嵌入式管理單元**。  

3.  在 [新增/移除嵌入式管理單元] 對話方塊中，在**獨立**索引標籤上，按一下**新增**。  

4.  在 [新增獨立嵌入式管理單元] 對話方塊中，選取**憑證**嵌入式管理單元從**可用的獨立嵌入式管理單元**清單，然後再按**新增**。  

5.  在 [憑證嵌入式管理單元對話方塊中，選取**我的使用者帳戶**，然後按一下**下一步]**。  

6.  在 [選取電腦] 對話方塊中，按一下**完成**。  

7.  在 [新增獨立嵌入式管理單元] 對話方塊中，按一下**關閉**。  

8.  在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**確定**。  

9. 在 [Console1] 視窗中，依序展開**Certificates (Local Computer)**，展開**個人**，然後按一下**憑證**。  

10. 在右窗格中，以滑鼠右鍵按一下**Fabrikam Encryption**憑證，指向**所有工作**，然後按一下**匯出**。  

11. 在 **歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。  

12. 在上**匯出私密金鑰**頁面上，選取 **[是，匯出私密金鑰**，然後按一下**下一步]**。  

13. 在 **匯出檔案格式**頁面上，請確定**個人資訊交換**是唯一選取的選項，然後按一下 **下一步**。  

14. 在上**密碼**頁面上，於**密碼**並**確認密碼**方塊中，輸入**mysecret**，然後按一下 [**下一步]**.  

15. 在 **要匯出的檔案**頁面上，按一下**瀏覽**。  

16. 在 **另存新檔**對話方塊中，使用檔案路徑的憑證儲存*\<磁碟機\>*: \Certs\Fabrikam Private Encryption.pfx。  

17. 在 [**要匯出的檔案**頁面上，按一下**下一步]**。  

18. 在 **完成 憑證匯出精靈**頁面上，按一下**完成**。  

19. 在 [憑證匯出精靈] 快顯視窗表示匯出成功，按一下**確定**。  

20. 針對 Fabrikam Signature 憑證重複執行步驟 10-19，並另存為 Fabrikam Private Signature.pfx 檔名。  

21. 針對 Contoso Signature 憑證和 Contoso Encryption 憑證重複執行步驟 10-19，並分別另存為 Contoso Private Signature.pfx 及 Contoso Private Encryption.pfx。  

### <a name="to-generate-public-certificates-for-the-encryption-and-signature-certificates"></a>為加密憑證及簽章憑證產生公開憑證  

1.  在 [Console1] 視窗中，依序展開**憑證-目前使用者**，展開**個人**，然後按一下**憑證**。  

2.  以滑鼠右鍵按一下**Fabrikam Encryption**憑證，指向**所有工作**，然後按一下**匯出**。  

3.  在 **歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。  

4.  在 [**匯出私密金鑰**頁面上，選取**否，不要匯出私密金鑰**，然後按一下**下一步]**。  

5.  在 [**匯出檔案格式**頁面上，按一下**下一步]**。  

6.  在 **要匯出的檔案**頁面上，按一下**瀏覽**。  

7.  在 [另存新檔] 對話方塊中，輸入**\<磁碟機\>: \Certs** for**儲存在**， **Fabrikam Public Encryption.cer**為**檔案名稱**，並 **\*.cer**如**存檔類型**，然後按一下**儲存**。  

8.  在 [**要匯出的檔案**頁面上，按一下**下一步]**。  

9. 在 **完成 憑證匯出精靈**頁面上，按一下**完成**。  

10. 在 [憑證匯出精靈] 快顯視窗表示匯出成功，按一下**確定**。  

11. 針對 Fabrikam 簽章憑證重複執行步驟 1-9，並另存為 Fabrikam Public Signature.cer 檔名。  

12. 針對 Contoso Signature 憑證和 Contoso Encryption 憑證重複執行步驟 1-9，並分別另存為 Contoso Public Signature.cer 及 Contoso Public Encryption.cer。  

## <a name="see-also"></a>另請參閱  
 [步驟 3：匯入公開憑證與私用憑證](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)