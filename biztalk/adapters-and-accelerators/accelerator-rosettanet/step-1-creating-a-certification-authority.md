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
# <a name="step-1-creating-a-certification-authority"></a>步驟 1： 建立憑證授權單位
在本主題中，您將安裝憑證服務 [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 元件。 您可以使用此元件產生必要的憑證，以促成 Contoso 和 Fabrikam 組織之間的安全通訊。 每個交易夥伴都會有可用來通訊的私人加密憑證，以及用於識別身份的私人簽章憑證。 此外，交易夥伴將彼此共用公開金鑰憑證，以便在實作 3A2 交易夥伴介面程序 (PIP) 時保護彼此之間的通訊。  
  
### <a name="to-install-the-certificate-server"></a>安裝憑證伺服器  
  
1.  按一下**啟動**，指向 **設定**，然後按一下 **控制台**。 按兩下**新增或移除程式**。  
  
2.  在**新增或移除程式**對話方塊中，按一下 **新增/移除 Windows 元件**。  
  
3.  上**Windows 元件精靈**頁面上，於**元件**區段中，選取**憑證服務**，按一下 **是**，然後按一下**下一步**啟動設定元件精靈。  
  
    > [!NOTE]
    >  如果**憑證 ServicesWindows**元件已經選取，請略過此程序的其餘部分。  
  
4.  在**CA 類型**頁面上，請確定**獨立根 CA**已選取，然後按一下**下一步**。  
  
5.  在**CA 識別資訊**頁面上，於**此 CA 的一般名稱**方塊中，輸入**Contoso-fabrikamca**，然後按一下 **下一步**。  
  
6.  在**憑證資料庫設定**頁面上，保留預設值，然後按**下一步**。  
  
7.  按一下**是**時精靈會提示您停止 Internet Information Services (IIS)。  
  
8.  按一下**是**如果**設定元件精靈**會提示您啟用 Active Server Pages。  
  
9. 按一下**完成**關閉**Windows 元件精靈**。  
  
    > [!NOTE]
    >  您只需要使用一台電腦做為憑證授權單位， 不必在另一台電腦上重複執行此步驟。 本教學課程使用 Contoso 電腦做為憑證授權單位。  
  
### <a name="to-install-a-root-certification-authority-ca-for-windows-server-2008"></a>若要安裝 Windows Server 2008 的根憑證授權單位 (CA)  
  
1.  開啟 伺服器管理員中，按一下**新增角色**在角色中，按一下 **下一步**，然後按一下**Active Directory 憑證**服務 核取方塊。 按一下**下一步**兩次。  
  
2.  在 選取角色服務頁面上，按一下 **憑證授權單位和憑證授權單位網頁註冊**。 按一下 **[下一步]**。  
  
3.  在 指定安裝類型 頁面上，按一下 **獨立**。 按一下 **[下一步]**。  
  
4.  在 指定 CA 類型 頁面中，按一下 根 CA。 按一下 **[下一步]**。  
  
5.  在 [安裝私密金鑰] 頁面上，按一下 [建立新的私密金鑰]。 按一下 **[下一步]**。  
  
6.  在 [設定 CA 的密碼編譯] 頁面上， 按一下 **[下一步]**。  
  
7.  設定 CA 名稱 上的一般名稱，這個 CA 方塊中，輸入 Contoso-fabrikamca，，然後按一下**下一步**。  
  
8.  在 設定有效期間 頁面上，按一下 **下一步**。  
  
9. 在 設定憑證資料庫 頁面上，按一下 **下一步**。  
  
10. 在 確認安裝選項 頁面上，按一下 **安裝**。  
  
### <a name="configuring-the-web-site-for-the-ca-to-use-https-authentication"></a>設定 CA 的網站使用 HTTPS 驗證  
  
1.  在您當做憑證授權單位使用的電腦上，按一下 [開始]，指向 [所有程式]，再指向 [系統管理工具]，然後按一下 [網際網路資訊服務 (IIS) 管理員]。  
  
2.  在 [網際網路資訊服務 (IIS) 管理員] 對話方塊中，以滑鼠右鍵按一下**預設的網站和選取編輯繫結...** 從快顯功能表。  
  
3.  在站台繫結 對話方塊中按一下**新增**。  
  
4.  在 新增網站繫結 對話方塊中選取**https**在 類型 下拉式清單，選取從憑證**SSL 憑證**下拉式清單，然後按一下 **確定**。  
  
5.  按一下**關閉**關閉站台繫結... 對話方塊。  
  
### <a name="to-download-the-ca-certificate"></a>若要下載 CA 憑證  
  
1.  在 Internet Explorer 中，找出並開啟 http://<contoso_computername>/certsrv/Default.asp。  
  
2.  在 Default.asp 頁面上，按一下 **下載 CA 憑證、 憑證鏈結或 CRL**。  
  
3.  請確定**目前 [Contoso-fabrikamca]**中選取**CA 憑證**清單，然後再按**下載 CA 憑證**。  
  
4.  在 Contoso 和 Fabrikam 電腦上都將憑證儲存為 C:\Certs\Contoso-FabrikamCA.cer。  
  
### <a name="to-import-the-ca-certificate-to-the-trusted-root-certification-authorities-store"></a>將 CA 憑證匯入至受信任的根憑證授權單位存放區  
  
1.  按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。  
  
2.  在命令提示字元中，移至**\<磁碟機 >: \Program Files\MicrosoftBizTalk\<版本 > Accelerator for RosettaNet\SDK**，然後按下**Enter**。  
  
3.  在命令提示字元中，輸入**CertWizard /Rootkey"\<磁碟機 >: \Certs\Contoso-FabrikamCA.cer"**，然後按下**Enter**。  
  
    > [!IMPORTANT]
    >  在 Contoso 和 Fabrikam 兩台電腦執行此程序。  
  
### <a name="to-enable-automatic-certificate-issuing"></a>啟用自動憑證核發  
  
1.  在做為憑證授權單位的電腦，按一下**啟動**，指向 **程式**，指向 **系統管理工具**，然後按一下  **憑證授權單位**。  
  
2.  在 憑證授權單位 對話方塊中，以滑鼠右鍵按一下**Contoso-fabrikamca**，然後按一下 **屬性**。  
  
3.  在 Contoso-fabrikamca 內容 對話方塊上**原則模組**索引標籤上，按一下 **屬性**。  
  
4.  在 屬性 對話方塊中，選取**遵循憑證範本中的設定**，然後按一下 **確定**。  
  
5.  按一下**確定**以關閉 [Contoso-fabrikamca] 對話方塊。  
  
6.  關閉 [憑證授權單位] 對話方塊。  
  
    > [!NOTE]
    >  啟用自動憑證核發之後，憑證服務便會自動化憑證核發程序。 您必須重新啟動憑證服務，使這個變更生效。  
    >   
    >  您可能需要將根憑證 Contoso-FabrikamCA.cer 安裝在 Current User\Trusted Root Certification authorities 中。  
  
## <a name="see-also"></a>另請參閱  
 [步驟 2： 建立公開憑證與私用憑證](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)