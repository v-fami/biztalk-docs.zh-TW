---
title: "如何安裝憑證，以便讓 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70a89595-8828-4872-b78b-77e9b0b048b8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d799956d25bfe8e494fcbc2fbc6cbea770a92fdb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-install-certificates-for-biztalk-server"></a>如何安裝 BizTalk Server 的憑證
在傳送以協助保護資料[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您必須將適當的憑證新增至適當的憑證存放區中，並將憑證與適當的 BizTalk 成品產生關聯。 本主題說明如何顯示憑證管理主控台介面的本機電腦和目前的使用者憑證存放區，以及如何在適當的存放區中安裝適當的憑證。  
  
 下表中所顯示的憑證可用來協助登、 驗證簽章、 加密和解密訊息。  
  
|憑證使用方式|憑證類型|憑證存放區|  
|-----------------------|----------------------|-----------------------|  
|簽章 (輸出)|自有私密金鑰 (.pfx)|目前的使用者\\<br />每個 BizTalk 伺服器裝載 MIME/SMIME 編碼器管線做為每個主控件執行個體服務帳戶的個人存放區|  
|簽章驗證 (輸入)|交易夥伴的公開金鑰 (.cer)|每個 BizTalk Server 的「本機電腦\其他人」存放區，該伺服器裝載 MIME/SMIME 解碼器管線做為每個主控件執行個體服務帳戶|  
|加密 (輸出)|交易夥伴的公開金鑰 (.cer)|每個裝載 MIME/SMIME 編碼器管線之 BizTalk Server 的「本機電腦\其他人」存放區|  
|解密 (輸入)|自有私密金鑰 (.pfx)|每個 BizTalk Server 的「目前使用者\個人」存放區，該伺服器裝載 MIME/SMIME 解碼器管線做為每個主控件執行個體服務帳戶|  
  
## <a name="prerequisites"></a>必要條件  
 您必須以成員的登入本主題中執行的程序[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組。  
  
### <a name="to-display-the-certificates-management-console"></a>若要顯示憑證管理主控台  
  
1.  按一下**啟動**，按一下**執行**，型別**MMC**，按一下**確定**開啟**Microsoft Management Console**.  
  
2.  按一下**檔案**功能表，然後再按一下**新增或移除嵌入式管理單元**顯示**新增或移除嵌入式管理單元** 對話方塊。  
  
3.  按一下**新增** 按鈕以顯示**新增獨立嵌入式管理單元** 對話方塊。  
  
4.  選取**憑證**從嵌入式管理單元，然後再按一下清單**新增**。  
  
5.  選取**電腦帳戶**，按一下 **下一步**，然後按一下 **完成**。 這會新增**憑證管理主控台**介面**本機電腦**。  
  
6.  請確認**憑證**仍然有選取的嵌入式管理單元清單，然後按一下 **新增**一次。  
  
7.  選取**我的使用者帳戶**，然後按一下 **完成**。 這會新增**憑證管理主控台**介面**目前使用者**。  
  
    > [!NOTE]  
    >  這會顯示**憑證管理主控台**您目前為登入的帳戶。 如果您需要針對某個服務帳戶將憑證匯入「個人」存放區，您應該先使用該服務帳戶認證來登入。  
  
8.  按一下**關閉**按鈕**獨立嵌入式管理單元** 對話方塊。  
  
9. 按一下**確定**按鈕**新增或移除嵌入式管理單元** 對話方塊。  
  
### <a name="to-install-a-certificate-for-receiving-encrypted-messages"></a>若要安裝的憑證來接收加密的訊息  
  
1.  要求的憑證授權單位 (CA) 的數位簽章的私密-公開金鑰組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用。  
  
2.  傳送給夥伴的公開金鑰進行加密。  
  
3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，執行的處理常式的主控件執行個體的服務帳戶將會從夥伴接收訊息的身分登入。 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]私密金鑰憑證用於解密服務帳戶的個人存放區中的訊息。  
  
    > [!NOTE]  
    >  如需有關用來安裝憑證進行加密程序的詳細資訊，請參閱[如何安裝加密訊息的憑證](http://go.microsoft.com/fwlink/?LinkId=155156)(http://go.microsoft.com/fwlink/?LinkId=155156) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。 如需此工具用來將憑證匯入憑證存放區的詳細資訊，請參閱[憑證精靈公用程式](http://go.microsoft.com/fwlink/?LinkId=155157)(http://go.microsoft.com/fwlink/?LinkId=155157) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
4.  已安裝協力廠商[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]公開金鑰憑證來加密適當的存放區中的訊息。 如果夥伴正在使用 Windows 2000 Server、 Windows Server 2003 或 Windows Server 2008，它們應該在其他人存放區中安裝公開金鑰。  
  
### <a name="to-install-a-certificate-for-sending-encrypted-messages"></a>若要安裝的憑證傳送加密的訊息  
  
1.  有協力廠商憑證授權單位 (CA) 要求加密的私密-公開金鑰組。  
  
2.  已將其公開金鑰來加密傳送給夥伴的訊息傳送給您的夥伴。  
  
3.  已安裝適當的存放區中的訊息解密的私用金鑰憑證的協力電腦。 如果夥伴正在使用 Windows 2000 Server、 Windows Server 2003 或 Windows Server 2008，它們應該在個人憑證存放區中安裝私密金鑰。  
  
    > [!NOTE]  
    >  如需有關用來安裝憑證進行加密程序的詳細資訊，請參閱[如何安裝加密訊息的憑證](http://go.microsoft.com/fwlink/?LinkId=155156)(http://go.microsoft.com/fwlink/?LinkId=155156) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。 如需此工具用來將憑證匯入憑證存放區的詳細資訊，請參閱[憑證精靈公用程式](http://go.microsoft.com/fwlink/?LinkId=155157)(http://go.microsoft.com/fwlink/?LinkId=155157) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
4.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，登入已執行的處理常式將會傳送訊息給夥伴的主控件執行個體的伺服器。 安裝夥伴的公開金鑰憑證來加密傳送給其他人存放區中的交易夥伴的訊息。  
  
### <a name="to-install-a-certificate-for-receiving-signed-messages"></a>若要安裝的憑證來接收簽署的訊息  
  
1.  有協力廠商憑證授權單位 (CA) 要求數位簽章的私密-公開金鑰組。  
  
2.  已將其數位簽章的公開金鑰傳送給您的夥伴。  
  
3.  已安裝其私密金鑰憑證來簽署訊息的適當存放區中的夥伴。 如果他們使用的 Windows 2000 Server、 Windows Server 2003 或 Windows Server 2008，讓它們將會簽署訊息傳送至帳戶的個人存放區中安裝私密金鑰[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    > [!NOTE]  
    >  如需有關用來安裝憑證進行加密程序的詳細資訊，請參閱[如何安裝加密訊息的憑證](http://go.microsoft.com/fwlink/?LinkId=155156)([http://go.microsoft.com/fwlink/?LinkId=155156](http://go.microsoft.com/fwlink/?LinkId=155156)) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。 如需此工具用來將憑證匯入憑證存放區的詳細資訊，請參閱[憑證精靈公用程式](http://go.microsoft.com/fwlink/?LinkId=155157)(http://go.microsoft.com/fwlink/?LinkId=155156) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
4.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，登入有執行將會從夥伴接收訊息的處理常式的主控件執行個體的伺服器。 安裝夥伴的公開金鑰憑證來驗證其簽章中的其他人存放區。  
  
### <a name="to-install-a-certificate-for-sending-signed-messages"></a>若要安裝的憑證來傳送簽署的訊息  
  
1.  要求的憑證授權單位 (CA) 的數位簽章的私密-公開金鑰組[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用。  
  
2.  數位簽章的公開金鑰傳送給夥伴。  
  
3.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，執行的處理常式的主控件執行個體的服務帳戶會傳送訊息給夥伴身分登入。 安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]私密金鑰憑證來簽署訊息的服務帳戶的個人存放區。  
  
    > [!NOTE]  
    >  如需有關用來安裝憑證進行加密程序的詳細資訊，請參閱[如何安裝加密訊息的憑證](http://go.microsoft.com/fwlink/?LinkId=155156)(http://go.microsoft.com/fwlink/?LinkId=155156) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。 如需此工具用來將憑證匯入憑證存放區的詳細資訊，請參閱[憑證精靈公用程式](http://go.microsoft.com/fwlink/?LinkId=155157)(http://go.microsoft.com/fwlink/?LinkId=155157) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
4.  已安裝協力廠商[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]公開金鑰憑證來驗證數位簽章中適當的存放區。 如果夥伴正在使用 Windows 2000 Server、 Windows Server 2003 或 Windows Server 2008，它們應該在其他人存放區中安裝公開金鑰。