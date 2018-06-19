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
# <a name="step-2-creating-public-and-private-certificates"></a>步驟 2： 建立公開憑證與私用憑證
在此步驟中，您可以使用憑證授權單位中建立[步驟 1： 建立憑證授權單位 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md)以產生 Contoso 及 Fabrikam 組織使用的公用和私用憑證。  
  
### <a name="to-generate-the-contoso-and-fabrikam-encryption-certificates"></a>產生 Contoso 及 Fabrikam 加密憑證  
  
1.  在當做憑證授權單位使用的電腦上，於 Internet Explorer 中找出並且開啟 http://<contoso_computername>/certsrv。  
  
2.  在**歡迎**頁面上，按一下**要求憑證**。  
  
3.  在**要求憑證**頁面上，按一下**進階的憑證要求**。  
  
4.  在**進階憑證要求**頁面上，按一下**建立並提交一個要求向這個 CA**。  
  
5.  在**進階憑證要求**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Fabrikam Encryption**。|  
    |**電子郵件**|型別 **jdoe@fabrikam.com** 。|  
    |**公司**|型別**Fabrikam**。|  
    |**部門**|型別**測試**。|  
    |**City**|型別**測試**。|  
    |**State**|型別**測試**。|  
    |**國家/地區**|型別**美國**。|  
    |**需要的憑證類型**|選取**電子郵件保護憑證**從下拉式清單。|  
    |**金鑰使用方法**|選取**Exchange**選項。|  
    |**其他金鑰選項**|核取下列選項：<br /><br /> -   **將金鑰標示成可匯出**<br />-   **將憑證儲存在本機電腦憑證存放區**|  
    |**易記名稱**|型別**Fabrikam Encryption**。|  
  
6.  按一下**送出**，然後按一下 [**是**中**Web 存取確認**] 對話方塊。  
  
7.  在**憑證核發**頁面上，按一下**安裝這個憑證**。  
  
8.  重複步驟 1-7 中的資訊變更**名稱**方塊中**識別資訊**區段和**易記名稱**方塊**Contoso加密**。  
  
### <a name="to-generate-the-contoso-and-fabrikam-signing-certificates"></a>產生 Contoso 及 Fabrikam 簽章憑證  
  
1.  在 Internet Explorer 中，尋找及開啟 http://<contoso_computername>/certsrv。  
  
2.  在**歡迎**頁面上，按一下**要求憑證**。  
  
3.  在**要求憑證**頁面上，按一下**進階的憑證要求**。  
  
4.  在**進階憑證要求**頁面上，按一下**建立並提交一個要求向這個 CA**。  
  
5.  在**進階憑證要求**頁面上，執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**名稱**|型別**Fabrikam Signature**。|  
    |**電子郵件**|型別 **jdoe@fabrikam.com** 。|  
    |**公司**|型別**Fabrikam**。|  
    |**部門**|型別**測試**。|  
    |**City**|型別**測試**。|  
    |**State**|型別**測試**。|  
    |**國家/地區**|型別**美國**。|  
    |**需要的憑證類型**|選取**電子郵件保護憑證**從下拉式清單。|  
    |**金鑰使用方法**|選取**簽章**選項。|  
    |**其他金鑰選項**|核取下列選項：<br /><br /> -   **將金鑰標示成可匯出**<br />-   **將憑證儲存在本機電腦憑證存放區**|  
    |**易記名稱**|型別**Fabrikam Signature**。|  
  
6.  按一下**送出**，然後按一下 **是**當詢問要求憑證。  
  
7.  在**憑證核發**頁面上，按一下**安裝這個憑證**。  
  
8.  重複步驟 1-7 中的資訊變更**名稱**方塊中**識別資訊**區段和**易記名稱**方塊**Contoso簽章**。  
  
### <a name="to-generate-private-certificates-for-the-encryption-and-signature-certificates"></a>為加密憑證及簽章憑證產生私用憑證  
  
1.  按一下**啟動**，按一下 **執行**，型別**MMC**，然後按一下 **確定**。  
  
2.  在 Console1 視窗上**檔案**功能表上，按一下 **新增/移除嵌入式管理單元**。  
  
3.  在 新增/移除嵌入式管理單元 對話方塊中，在**獨立**索引標籤上，按一下 **新增**。  
  
4.  在 [新增獨立嵌入式管理單元] 對話方塊中，選取**憑證**嵌入式管理單元從**可用的獨立嵌入式管理單元**清單，然後再按**新增**。  
  
5.  在 憑證嵌入式管理單元對話方塊中，選取**我的使用者帳戶**，然後按一下 **下一步**。  
  
6.  在 選取電腦 對話方塊中，按一下 **完成**。  
  
7.  在 [新增獨立嵌入式管理單元] 對話方塊中，按一下**關閉**。  
  
8.  在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**確定**。  
  
9. 在 主控台 1 視窗中，展開**憑證 （本機電腦）**，依序展開**個人**，然後按一下 **憑證**。  
  
10. 在右窗格中，以滑鼠右鍵按一下**Fabrikam Encryption**憑證，指向**所有工作**，然後按一下 **匯出**。  
  
11. 在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。  
  
12. 在**匯出私密金鑰**頁面上，選取**是，匯出私密金鑰**，然後按一下 **下一步**。  
  
13. 在**匯出檔案格式**頁面上，請確定**個人資訊交換**是唯一選取的選項，然後按一下**下一步**。  
  
14. 在**密碼**頁面上，於**密碼**和**確認密碼**方塊中，輸入**mysecret**，然後按一下 [**下一步]**.  
  
15. 在**要匯出的檔案**頁面上，按一下**瀏覽**。  
  
16. 在**存**對話方塊中，使用的檔案路徑的憑證儲存*\<磁碟機\>*: \Certs\Fabrikam Private Encryption.pfx。  
  
17. 在**要匯出的檔案**頁面上，按一下**下一步**。  
  
18. 在**完成憑證匯出精靈**頁面上，按一下**完成**。  
  
19. 在 憑證匯出精靈 快顯視窗表示匯出成功，按一下 **確定**。  
  
20. 針對 Fabrikam Signature 憑證重複執行步驟 10-19，並另存為 Fabrikam Private Signature.pfx 檔名。  
  
21. 針對 Contoso Signature 憑證和 Contoso Encryption 憑證重複執行步驟 10-19，並分別另存為 Contoso Private Signature.pfx 及 Contoso Private Encryption.pfx。  
  
### <a name="to-generate-public-certificates-for-the-encryption-and-signature-certificates"></a>為加密憑證及簽章憑證產生公開憑證  
  
1.  在 主控台 1 視窗中，展開**憑證 – 目前使用者**，依序展開**個人**，然後按一下 **憑證**。  
  
2.  以滑鼠右鍵按一下**Fabrikam Encryption**憑證，指向**所有工作**，然後按一下 **匯出**。  
  
3.  在**歡迎使用 憑證匯出精靈**頁面上，按一下**下一步**。  
  
4.  在**匯出私密金鑰**頁面上，選取**否，不要匯出私密金鑰**，然後按一下 **下一步**。  
  
5.  在**匯出檔案格式**頁面上，按一下**下一步**。  
  
6.  在**要匯出的檔案**頁面上，按一下**瀏覽**。  
  
7.  在 另存新檔 對話方塊中，輸入**\<磁碟機\>: \Certs**如**存**， **Fabrikam Public Encryption.cer**為**檔案名稱**，和 **\*.cer**如**存檔類型**，然後按一下 **儲存**。  
  
8.  在**要匯出的檔案**頁面上，按一下**下一步**。  
  
9. 在**完成憑證匯出精靈**頁面上，按一下**完成**。  
  
10. 在 憑證匯出精靈 快顯視窗表示匯出成功，按一下 **確定**。  
  
11. 針對 Fabrikam 簽章憑證重複執行步驟 1-9，並另存為 Fabrikam Public Signature.cer 檔名。  
  
12. 針對 Contoso Signature 憑證和 Contoso Encryption 憑證重複執行步驟 1-9，並分別另存為 Contoso Public Signature.cer 及 Contoso Public Encryption.cer。  
  
## <a name="see-also"></a>請參閱  
 [步驟 3：匯入公開憑證與私用憑證](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)