---
title: "設定 MIME 或 SMIME 訊息的憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea6e5481-fc2e-4b17-b6c8-1ec5d2bfa2c3
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 72fb8677734cc5a3e87d9b3c90618f719430c553
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-certificates-for-mime-or-smime-messages"></a>設定 MIME 或 SMIME 訊息的憑證
在傳送以協助保護資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須將與適當的 BizTalk 成品的憑證存放區中安裝的憑證產生關聯。 這適用於 MIME/SMIME 編碼訊息。 它也適用於 AS2 傳輸，傳輸 MIME/SMIME 訊息。  
  
 憑證使用方式案例和組態的可用選項中，使用下表做為參考[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本主題結尾處的 「 在此區段 」 標題中所列的主題會提供詳細程序。  
  
|**憑證使用方式**|**使用者內容**|**憑證存放區位置**|**憑證類型**|**在 BizTalk 管理主控台中設定參數**|  
|---------------------------|----------------------|------------------------------------|--------------------------|------------------------------------------------------------------------|  
|加密 (傳送)|與傳送處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將要裝載 S/MIME 編碼器管線，並加密憑證匯入**本機電腦 \ 其他人**儲存。|交易夥伴公用憑證|-指定的加密憑證值**一般名稱**和**指紋**上**憑證**頁面**傳送埠屬性** 對話方塊。<br />指定管線**編碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**傳送管線**下拉式清單上的**一般**頁面**傳送連接埠內容** 對話方塊。|  
|解密 (接收)|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，server 將要裝載 S/MIME 解碼器管線做為每個主控件執行個體服務帳戶 」，並將解密憑證匯入**目前使用者 \ 個人**儲存。 **注意：**解密管線在執行 IIS 6.0 的電腦上成功完成，或更新版本中，確定 IIS 應用程式集區帳戶和相關聯的接收處理常式的主控件執行個體所使用的帳戶都相同，而且此帳戶是成員的\< *machineName*> \IIS_WPG 群組。 如需有關設定 IIS 處理序識別如 IIS，請參閱[解決 IIS 權限問題的指導方針](http://go.microsoft.com/fwlink/?LinkId=155161)(http://go.microsoft.com/fwlink/?LinkId=155161) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。 這些處理序必須在相同的帳戶下執行，以確保可載入帳戶設定檔，而這樣會載入在管線中執行解密所需的登錄機碼。 基於效能考量，IIS 時並未載入帳戶設定檔啟動關聯的 w3wp.exe 處理序因此[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件執行個體必須使用相同的帳戶來設定以便[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會載入帳戶設定檔和登錄機碼。|自有私用憑證|-指定的解密憑證值**一般名稱**和**指紋**上**憑證**每個頁面**主控件屬性** 對話方塊。<br />指定管線**解碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**接收管線**下拉式清單上的**一般**頁面**接收位置屬性** 對話方塊。|  
|簽章 (傳送)|與傳送處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，server 將要裝載 S/MIME 編碼器管線做為每個主控件執行個體服務帳戶 」，並將簽章憑證匯入**目前使用者 \ 個人**儲存。|自有私用憑證|-指定的簽章憑證值**一般名稱**和**指紋**上**憑證**頁面**BizTalk 群組屬性** 對話方塊。 **注意：**只有一個簽章憑證可以指定每個[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]群組。<br />指定管線**編碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**傳送管線**下拉式清單上的**一般**頁面**傳送連接埠內容** 對話方塊。|  
|簽章驗證 (接收)|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將要裝載 S/MIME 解碼器管線，並將簽章憑證匯入**本機電腦 \ 其他人**儲存。|交易夥伴公用憑證|-指定的驗證憑證值**一般名稱**和**指紋**上**憑證**每個頁面**合作對象屬性** 對話方塊。<br />指定管線**解碼**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**接收管線**下拉式清單上的**一般**頁面**接收位置屬性** 對話方塊。 **注意：**用來驗證合作對象必須是唯一的憑證來驗證其他合作對象的簽章的簽章的憑證。 **注意：**組態**解碼**選項必須部署具有 MIME/SMIME 解碼器元件的管線。|  
|合作對象解析 (接收)|與接收處理常式關聯之主控件執行個體所使用的帳戶|登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]電腦從合作對象解析正在設定時，與匯入憑證**本機電腦 \ 其他人**儲存。|交易夥伴公用憑證|-指定的憑證值**一般名稱**和**指紋**上**憑證**每個頁面**主控件屬性**對話方塊.<br />-指定**解析合作對象**中選項**設定管線** 對話方塊。 **設定管線**旁按一下按鈕會顯示對話方塊**接收管線**下拉式清單上的**一般**頁面**接收位置屬性** 對話方塊。 **注意：**此選項的組態需要使用包含管線**合作對象解析**元件。 **XMLReceive**管線包含**合作對象解析**元件。|  
|HTTPS (傳送)|與傳送處理常式關聯之主控件執行個體所使用的帳戶|SSL 通訊不需要用戶端憑證。 是否需要用戶端憑證是由目的地 Web 伺服器管理員自由決定。 如果目的地 Web 伺服器需要用戶端憑證，請遵循下列步驟：<br /><br /> -從交易夥伴取得公用憑證。<br />-登入執行每一部電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]為相關聯的傳送處理常式的主控件執行個體所使用的帳戶。<br />匯入憑證**目前使用者 \ 個人**儲存。<br /><br /> 如需設定 IIS 以使用 SSL 的詳細資訊，請參閱知識庫文件[HOW TO： 安裝 Windows Server 2003 中的網頁伺服器上匯入的憑證](http://go.microsoft.com/fwlink/?LinkId=155162)(http://go.microsoft.com/fwlink/?LinkId=155162)。<br /><br /> 如需如何使用 Windows Server 2003 憑證服務網頁取得憑證資訊，請參閱[使用 Windows Server 2003 Certificate Services Web Pages](http://go.microsoft.com/fwlink/?LinkID=69975) (http://go.microsoft.com/fwlink/?LinkID=69975)。 **注意：**若要使用憑證服務網頁，從 Windows Server 2008 電腦取得憑證，請參閱 Microsoft 知識庫文章 922706 網址[http://go.microsoft.com/fwlink/?LinkId = 155317](http://go.microsoft.com/fwlink/?LinkId=155317) (http://go.microsoft.com/fwlink/?LinkId = 155317)。|交易夥伴公用憑證|-   **HTTP 傳輸**-設定**SSL 用戶端憑證指紋**選項**驗證** 索引標籤**HTTP 傳輸屬性**對話方塊. **HTTP 傳輸屬性**會顯示對話方塊，即可**設定**按鈕**一般**頁面**傳送埠屬性**  對話方塊。<br />-   **SOAP 傳輸**-設定**用戶端憑證指紋**選項**一般** 索引標籤**SOAP 傳輸屬性** 對話方塊。 **SOAP 傳輸屬性**會顯示對話方塊，即可**設定**按鈕**一般**頁面**傳送埠屬性**  對話方塊。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何設定 BizTalk Server 接收 MIME 加密或 SMIME 訊息](../technical-guides/how-to-configure-biztalk-server-to-receive-encrypted-mime-or-smime-messages.md)  
  
-   [如何設定 BizTalk Server 傳送加密的 MIME 或 SMIME 訊息](~/technical-guides/how-to-configure-biztalk-server-to-send-encrypted-mime-smime-messages.md)  
  
-   [如何設定 BizTalk Server 來接收簽署 MIME 或 SMIME 訊息](../technical-guides/how-to-configure-biztalk-server-to-receive-signed-mime-or-smime-messages.md)  
  
-   [如何設定 BizTalk Server 來傳送簽署 MIME 或 SMIME 訊息](../technical-guides/how-to-configure-biztalk-server-to-send-signed-mime-or-smime-messages.md)