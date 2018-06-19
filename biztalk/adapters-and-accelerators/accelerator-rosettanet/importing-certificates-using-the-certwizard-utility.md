---
title: 使用 CertWizard 公用程式匯入憑證 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- certificates, root keys
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- CertWizard utility
- certificates, importing
- root keys
ms.assetid: 0c54d7ab-69cf-4f4a-b976-6f740a41280b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64be28927a49a1fc751870785ff3fc3f55a36cb1
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
ms.locfileid: "26006839"
---
# <a name="importing-certificates-using-the-certwizard-utility"></a>使用 CertWizard 公用程式匯入憑證
本主題描述如何使用 CertWizard 公用程式，逐步命令列公用程式中使用匯入憑證[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK。 此主題討論如何匯入私密、公開或根金鑰， 以及用來設定憑證的切換參數。  
  
 CertWizard 公用程式可自動化許多步驟。否則，您必須使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) 手動執行這些步驟。 CertWizard 公用程式會執行**runas**命令，以開啟 MMC，以主控件服務帳戶。 如果您需要新增**Useridentity**參數，它會偵測並使用主控件服務帳戶，提示您輸入密碼。 此公用程式亦可儲存與設定憑證。  
  
 您可以建立包含多個 CertWizard 公用程式命令的批次檔，以便同時匯入多個憑證。  
  
### <a name="to-import-a-private-key"></a>匯入私密金鑰  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。  
  
2.  在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK** 。  
  
    > [!NOTE]
    >  如需 CertWizard 公用程式說明，請輸入**CertWizard /？** 在命令提示字元。  
  
3.  在命令提示字元中，輸入**CertWizard /Privatekey \<filename\>.pfx**，其中\< *filename*\>x 包含私用憑證。 若要提供檔案的密碼，附加 **/Filepassword \<filepassword\>** 命令。  
  
4.  如果您想要將憑證匯入特定 BizTalk 主控件所使用的帳戶、 新增 **/Useridentity \<useridentity\> /Password\<密碼\>** 命令。  
  
5.  如果您想要指定特定的憑證指紋，以防.pfx 檔案包含一個以上的憑證，附加 **/Thumbprint\<指紋\>** 命令。  
  
6.  如果您想要設定的憑證使用狀況，附加 **/Usage**命令，然後附加下列值之一：  
  
    -   附加**登**BizTalk 群組，做為簽署的憑證加入憑證的指紋。 為集合，在對話方塊中 BizTalk 管理主控台中的 Microsoft BizTalk Server （本機）。  
  
    -   附加**解密**以新增憑證的指紋作為解密憑證為 BizTalk 主控件所設定的屬性頁的 [憑證] 索引標籤上每個主控件在 BizTalk 管理主控台。  
  
    -   附加**兩者**新增憑證的指紋，這兩個 BizTalk 群組的簽署憑證和 BizTalk 主控件的解密憑證。  
  
    -   附加**無**當您不要設定 BizTalk 群組或 BizTalk 主控件的設定。  
  
7.  如果您想要設定成可匯出的憑證，將附加 **/exportable true**。 若要將憑證設為非可匯出，附加 **/exportable false**，這是預設行為。  
  
8.  按 **Enter**鍵。  
  
9. 若您未在命令中輸入所需密碼之一，工具會提示您輸入。 輸入密碼，然後按**Enter**。  
  
10. 若檔案包含多個憑證，但您未在命令中輸入憑證指紋，工具將顯示可用的憑證指紋，並提示您選取其中一個憑證指紋。 輸入您要的然後按下憑證指紋號碼**Enter**。  
  
     此工具將憑證匯入 \Personal\Certificates 存放區中指定的使用者 **/useridentity**切換。 若您未指定使用者，則預設使用者為 BizTalkServerApplication 與 BizTalkServerIsolatedHost 主控件的使用者身份識別。  
  
### <a name="to-import-a-public-key"></a>匯入公開金鑰  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。  
  
2.  在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK**。  
  
3.  在命令提示字元中，輸入**CertWizard /Publickey \<filename\>.cer**，其中\< *filename*\>包含公開憑證。  
  
4.  如果您想要指定憑證的.cer 或.der 檔案中的憑證指紋，附加 **/Thumbprint\<指紋\>** 命令。  
  
     這個工具會將憑證匯入 [憑證 (本機電腦)]\Other People\Certificates 存放區，並設定其組態。  
  
### <a name="to-import-a-root-key"></a>匯入根金鑰  
  
1.  按一下  **啟動**, ，按一下  **執行**, ，型別 **cmd**, ，然後按一下  **確定**。  
  
2.  在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK**。  
  
3.  在命令提示字元中，輸入**CertWizard /Rootkey \<filename\>.cer**，其中\< *filename*\>包含根憑證。  
  
4.  如果您想要指定憑證的.cer 或.der 檔案中的憑證指紋，附加 **/Thumbprint\<指紋\>** 命令。  
  
     這個工具會將憑證匯入 [憑證 (本機電腦)]\Trusted Root Certification Authority\Certificates 存放區，並設定其組態。  
  
## <a name="see-also"></a>另請參閱  
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)   
 [管理憑證](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)