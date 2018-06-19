---
title: 疑難排解憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7013db6-ebf7-4294-a072-e9b5b0ad0de2
caps.latest.revision: 26
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 963dfdd55937fd3e41fa50a5e2a609dd591f728f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25975964"
---
# <a name="troubleshooting-certificates"></a>憑證疑難排解
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以將公開金鑰基礎結構 (PKI) 數位憑證用於文件加密和解密作業、文件簽署和驗證 (不可否認性) 作業，以及用於合作對象解析作業。 本主題將描述各種憑證使用方式案例和組態選項，並提供搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用數位憑證的一些一般性指導方針。  
  
## <a name="certificate-usage-scenarios-and-configuration-options"></a>憑證使用方式案例和組態選項  
 在搭配 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用憑證時所發生的大多數問題，都是因為組態不正確或不完整所造成。 例如，將正確的憑證匯入錯誤的憑證存放區、將不正確的憑證匯入正確的存放區，或是未能將適當的資訊輸入到 BizTalk 管理主控台，將會造成使用憑證時發生執行階段錯誤。  
  
 使用下表當做 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中提供之憑證使用方式案例和組態選項的參考：  
  
|**憑證使用方式**|**使用者內容**|**憑證存放區位置**|**憑證類型**|**使用的管線元件**|**BizTalk Server 管理主控台中的組態參數**|  
|---------------------------|----------------------|------------------------------------|--------------------------|---------------------------------|-------------------------------------------------------------------------------|  
|加密 (傳送)|與傳送處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將要裝載 S/MIME 編碼器管線，並加密憑證匯入**本機電腦 \ 其他人**儲存。|交易夥伴公用憑證|MIME/SMIME 編碼器|-指定的加密憑證值**一般名稱**和**指紋**上**憑證**頁面**傳送埠屬性** 對話方塊。<br />指定管線**編碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**傳送管線**下拉式清單上的**一般**頁面**傳送連接埠內容** 對話方塊。|  
|解密 (接收)|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，server 將要裝載 S/MIME 解碼器管線做為每個主控件執行個體服務帳戶 」，並將解密憑證匯入**目前使用者 \ 個人**儲存。 **注意：** IIS 7.0 電腦上成功解密管線，請確認 IIS 應用程式集區帳戶和相關聯的接收處理常式的主控件執行個體所使用的帳戶都相同，而且此帳戶是的成員\<machineName\>\IIS_WPG 群組。 如需適用於 IIS 7.0 設定 IIS 處理序識別的詳細資訊，請參閱[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)。 這些處理序必須在相同的帳戶下執行，以確保可載入帳戶設定檔，而這樣會載入在管線中執行解密所需的登錄機碼。 基於效能的理由，IIS 6.0 在啟動關聯的 w3wp.exe 處理序時，並不會載入帳戶設定檔，如此一來，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體就必須設定相同的帳戶，好讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會載入帳戶設定檔和登錄機碼。|自有私用憑證|MIME/SMIME 解碼器|-指定的解密憑證值**一般名稱**和**指紋**上**憑證**每個頁面**主控件屬性** 對話方塊。<br />指定管線**解碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**接收管線**下拉式清單上的**一般**頁面**接收位置屬性** 對話方塊。|  
|簽章 (傳送)|與傳送處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，server 將要裝載 S/MIME 編碼器管線做為每個主控件執行個體服務帳戶 」，並將簽章憑證匯入**目前使用者 \ 個人**儲存。|自有私用憑證|MIME/SMIME 編碼器|-指定的簽章憑證值**一般名稱**和**指紋**上**憑證**頁面**BizTalk 群組屬性** 對話方塊。 **注意：** 只有一個簽章憑證可以指定每個[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]群組。<br />指定管線**編碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**傳送管線**下拉式清單上的**一般**頁面**傳送連接埠內容** 對話方塊。|  
|簽章驗證 (接收)|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將要裝載 S/MIME 解碼器管線，並將簽章憑證匯入**本機電腦 \ 其他人**儲存。|交易夥伴公用憑證|MIME/SMIME 解碼器|-指定的驗證憑證值**一般名稱**和**指紋**上**憑證**每個頁面**合作對象屬性** 對話方塊。<br />指定管線**解碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**接收管線**下拉式清單上的**一般**頁面**接收位置屬性** 對話方塊。 **注意：** 組態**解碼**選項必須部署具有 MIME/SMIME 解碼器元件的管線。|  
|合作對象解析 (接收)|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦從合作對象解析正在設定時，與匯入憑證**本機電腦 \ 其他人**儲存。|交易夥伴公用憑證|合作對象解析|-指定的憑證值**一般名稱**和**指紋**上**憑證**每個頁面**主控件屬性**對話方塊.<br />-指定**解析合作對象**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**接收管線**下拉式清單上的**一般**頁面**接收位置屬性** 對話方塊。 **注意：** 此選項的組態需要使用包含管線**合作對象解析**元件。 **XMLReceive**管線包含**合作對象解析**元件。|  
|HTTPS (傳送)|與傳送處理常式關聯之主控件執行個體所使用的帳戶|SSL 通訊不需要用戶端憑證。 是否需要用戶端憑證是由目的地 Web 伺服器管理員自由決定。 如果目的地 Web 伺服器需要用戶端憑證，請遵循下列步驟：<br /><br /> -從交易夥伴取得公用憑證。<br />-登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]為相關聯的傳送處理常式的主控件執行個體所使用的帳戶。<br />匯入憑證**目前使用者 \ 個人**儲存。<br /><br /> 如需如何使用 Windows Server 2008 憑證服務網頁取得憑證資訊，請參閱[要求憑證透過網頁](http://go.microsoft.com/fwlink/?LinkId=129628)。|交易夥伴公用憑證|NA|-   **HTTP 傳輸**-設定**SSL 用戶端憑證指紋**選項**驗證** 索引標籤**HTTP 傳輸屬性**對話方塊. **HTTP 傳輸屬性**會顯示對話方塊，即可**設定**按鈕**一般**頁面**傳送埠屬性**  對話方塊。<br />-   **SOAP 傳輸**-設定**用戶端憑證指紋**選項**一般** 索引標籤**SOAP 傳輸屬性** 對話方塊。 **SOAP 傳輸屬性**會顯示對話方塊，即可**設定**按鈕**一般**頁面**傳送埠屬性**  對話方塊。|  
  
#### <a name="to-display-the-certificates-management-console-interface-for-local-computer-and-current-user"></a>顯示 [本機電腦] 和 [目前使用者] 的 [憑證管理主控台] 介面  
  
1.  按一下**啟動**，按一下**執行**，型別**MMC**，按一下**確定**開啟**Microsoft Management Console**.  
  
2.  按一下**檔案**功能表，然後再按一下**新增/移除嵌入式管理單元**顯示**新增/移除嵌入式管理單元** 對話方塊。  
  
3.  選取**憑證**從可用的嵌入式管理單元，然後按一下清單**新增**。  
  
4.  選取**電腦帳戶**，按一下 **下一步**，然後按一下 **完成**。 這會新增**憑證管理主控台**介面**本機電腦**。  
  
5.  請確認**憑證**仍然有選取的嵌入式管理單元清單，然後按一下 **新增**一次。  
  
6.  選取**我的使用者帳戶**，然後按一下 **完成**。 這會新增**憑證管理主控台**介面**目前使用者**。  
  
    > [!NOTE]
    >  這會顯示**憑證管理主控台**您目前為登入的帳戶。 如果您需要針對某個服務帳戶將憑證匯入「個人」存放區，您應該先使用該服務帳戶認證來登入。  
  
7.  按一下**確定**按鈕**新增/移除嵌入式管理單元** 對話方塊。  
  
## <a name="general-guidelines"></a>一般指導方針  
  
-   **確定匯入的憑證用於其預期目的**： 若要這樣做，請連按兩下中的憑證**憑證管理主控台**介面，然後按一下 **詳細資料**  索引標籤**憑證** 對話方塊。 然後按一下 **所有**選項**顯示**下拉式清單，然後按一下以選取**金鑰使用方法**及/或**增強金鑰使用方法**欄位若要驗證的預定的用途。 如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 嘗試將憑證用於預期以外的用途，將會發生執行階段錯誤。  
  
-   **測試目標網站的連接**： 如果您使用 SSL，請確定您可以連接到目標網站，使用 Internet Explorer 再嘗試連線到目標網站，使用 HTTP 或 SOAP 傳輸。 請確認當您連接到目標網站時，會在 Internet Explorer 中顯示任何對話方塊。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]具有與連接到目標網站時，可能會顯示任何對話方塊互動機制。 對話方塊可能會顯示 Internet explorer，如果目標網站名稱不符合指定的 SSL 憑證中的網站名稱或根憑證授權單位，SSL 憑證不是在適當**受信任的根憑證授權單位**儲存。  
  
-   **使用 SSL 診斷工具分析 SSL 連接問題：** SSL 診斷工具是 IIS Diagnostics Toolkit 的選用元件。  下載 IIS Diagnostics Toolkit 從[Internet Information Services 診斷工具](http://go.microsoft.com/fwlink/?LinkId=64426)。  
  
-   **請確認憑證有效**。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會提示您如果憑證已過期。 相反地，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會擱置該訊息。  
  
## <a name="see-also"></a>請參閱  
 [加密和簽章憑證](../core/encryption-and-signing-certificates.md)