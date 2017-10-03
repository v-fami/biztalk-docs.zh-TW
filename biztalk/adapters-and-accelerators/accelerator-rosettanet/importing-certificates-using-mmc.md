---
title: "使用 MMC 匯入憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- certificates, importing
ms.assetid: 58fb1711-e295-4aa6-902e-e28e4a2cd921
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6030b711e0fd48d2632ff84428e1cb9ffc6e0402
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="importing-certificates-using-mmc"></a>使用 MMC 匯入憑證
本主題描述如何匯入的數位憑證[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]用以驗證交易夥伴、 解密內送訊息，或是加密或簽署外寄訊息。  
  
 此程序使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) 的「憑證」嵌入式管理單元。 此一手動程序將憑證匯入憑證存放區，並必須設定個別憑證的使用方式。 您也可以使用 CertWizard 公用程式匯入憑證。CertWizard 工具可為您自動設定憑證的使用方式。  
  
 若要匯入私用憑證，您必須以 BizTalk 主控件執行所用的使用者帳戶。  
  
### <a name="to-import-a-public-key-certificate"></a>匯入公開金鑰憑證  
  
1.  將公開金鑰 (.cer) 憑證檔案複製到目的伺服器硬碟上的位置。  
  
2.  按一下**啟動**，指向 **所有程式**，指向  **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]，然後按一下[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)]**管理主控台**.  
  
3.  在[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台中，展開 **憑證 （本機電腦）**。 登入的使用者必須具有電腦的管理權限。  
  
4.  以滑鼠右鍵按一下**其他人**，指向 **所有工作**，然後按一下 **匯入**。  
  
5.  在**憑證匯入精靈歡迎**頁面上，按一下**下一步**。  
  
6.  在**匯入檔案**頁面上，按一下**瀏覽**並找出包含憑證檔案的資料夾。 選取您想要匯入憑證，然後按一下的檔案**開啟**。  
  
7.  在**憑證存放區**頁面上，選取 **自動選取 根據憑證類型的憑證**或**將所有憑證都放入以下的存放區**. 如果您選取**將所有憑證都放入以下的存放區**，按一下**瀏覽**，選取憑證存放區，按一下**確定**，然後按一下 **下一步**.  
  
8.  按一下 **[完成]**。  
  
### <a name="to-import-a-private-key-certificate"></a>匯入私密金鑰憑證  
  
1.  將私密金鑰 (.pfx) 憑證檔案複製到目的伺服器硬碟上的位置。  
  
2.  按一下**啟動**，按一下**執行**，類型**執行身分 /user:\<裝載服務 > mmc**，然後按一下  **確定**。  
  
    > [!NOTE]
    >  如\<*裝載服務*>，輸入您在安裝時已自動選取的主機服務的服務名稱[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]。  
  
3.  輸入的密碼\<*裝載服務*>，然後按下**Enter**。  
  
4.  在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]管理主控台] 視窗上**檔案**功能表上，按一下 [**新增/移除嵌入式管理單元**。  
  
5.  在 [新增/移除嵌入式管理單元] 對話方塊中，按一下**新增**。  
  
6.  在 新增獨立嵌入式管理單元 對話方塊中，選取**憑證**，按一下**新增**，按一下 **關閉**，然後按一下 **確定**。  
  
7.  在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]管理主控台中，展開**憑證-目前使用者**，以滑鼠右鍵按一下**個人**，指向 **所有工作**，然後按一下  **匯入**。  
  
8.  在**憑證匯入精靈歡迎**頁面上，按一下**下一步**。  
  
9. 在**匯入檔案**頁面上，按一下**瀏覽**並找出包含您要匯入憑證的.pfx 憑證檔案所在的資料夾。 選取適當的檔案，然後按一下**開啟**。  
  
10. 在**密碼**頁面上，於**密碼**方塊中，輸入私密金鑰檔案的密碼。  
  
11. 選取**啟用加強私密金鑰保護**或**標示成可匯出此機碼**，然後按一下 **下一步**。  
  
12. 在**憑證存放區**頁面上，選取 **自動選取 根據憑證類型的憑證**或**將所有憑證都放入以下的存放區**. 如果您選取**將所有憑證都放入以下的存放區**，按一下**瀏覽**，選取存放區，按一下**確定**，然後按一下 **下一步**。  
  
13. 在**完成憑證匯入精靈**頁面上，按一下**完成**。  
  
## <a name="see-also"></a>另請參閱  
 [設定使用 MMC 匯入的憑證](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md)   
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)