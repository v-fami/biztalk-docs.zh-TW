---
title: 使用 CertWizard 公用程式匯入憑證 |Microsoft Docs
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
ms.openlocfilehash: 50bdce5ff094153e0aaa0e6ca69b106993722722
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993799"
---
# <a name="importing-certificates-using-the-certwizard-utility"></a>使用 CertWizard 公用程式匯入憑證
本主題描述如何使用 CertWizard 公用程式，逐步命令列公用程式可用於 Microsoft 匯入憑證[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]SDK。 此主題討論如何匯入私密、公開或根金鑰， 以及用來設定憑證的切換參數。  
  
 CertWizard 公用程式會自動執行許多步驟，您必須使用 Microsoft Management Console (MMC) 手動進行。 CertWizard 公用程式會執行**runas**命令來開啟 MMC，以主控件服務帳戶。 如果您未新增**Useridentity**參數，它會偵測並使用主控件服務帳戶，提示您輸入密碼。 此公用程式亦可儲存與設定憑證。  
  
 您可以建立包含多個 CertWizard 公用程式命令的批次檔，以便同時匯入多個憑證。  
  
### <a name="to-import-a-private-key"></a>匯入私密金鑰  
  
1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK** 。  
  
   > [!NOTE]
   >  使用 CertWizard 公用程式的說明，請輸入**CertWizard /？** 在命令提示字元。  
  
3. 在命令提示字元中，輸入**CertWizard /Privatekey\<檔名\>.pfx**，其中\< *filename*\>.pfx 包含私用憑證。 若要提供檔案的密碼，將附加 **/Filepassword \<filepassword\>** 命令。  
  
4. 如果您想要將憑證匯入 BizTalk 主控件所使用的特定帳戶，附加 **/Useridentity \<useridentity\> /Password\<密碼\>** 命令。  
  
5. 如果您想要指定特定的憑證指紋，以防.pfx 檔案包含一個以上的憑證、 附加 **/Thumbprint\<指紋\>** 命令。  
  
6. 如果您想要設定憑證的使用方式，將附加 **/Usage**命令，然後附加下列值之一：  
  
   -   附加**號**做為簽署憑證的憑證的指紋加入 BizTalk 群組。 在 BizTalk 管理主控台中的 Microsoft BizTalk server （本機） 對話方塊上設定。  
  
   -   附加**解密**做為解密憑證加入憑證的指紋為 BizTalk 主控件中，為在 BizTalk 管理主控台中的每一部主機上的屬性頁的 [憑證] 索引標籤集合。  
  
   -   附加**兩者**新增憑證的指紋，這兩個 BizTalk 群組的簽署憑證和 BizTalk 主控件的解密憑證。  
  
   -   附加**無**時您不想設定 BizTalk 群組] 或 [BizTalk 主控件的設定。  
  
7. 如果您想要將憑證設定為可匯出，附加 **/exportable true**。 若要將憑證設為不可匯出，附加 **/exportable false**，這是預設行為。  
  
8. 按 **Enter**鍵。  
  
9. 若您未在命令中輸入所需密碼之一，工具會提示您輸入。 輸入密碼，然後按**Enter**。  
  
10. 若檔案包含多個憑證，但您未在命令中輸入憑證指紋，工具將顯示可用的憑證指紋，並提示您選取其中一個憑證指紋。 輸入的數目，然後再按下的憑證指紋**Enter**。  
  
     此工具將憑證匯入 \Personal\Certificates 存放區中指定的使用者 **/useridentity**切換。 若您未指定使用者，則預設使用者為 BizTalkServerApplication 與 BizTalkServerIsolatedHost 主控件的使用者身份識別。  
  
### <a name="to-import-a-public-key"></a>匯入公開金鑰  
  
1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾中的，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK**。  
  
3. 在命令提示字元中，輸入**CertWizard /Publickey\<檔名\>.cer**，其中\< *filename*\>.cer 包含公開憑證。  
  
4. 如果您想要指定憑證的.cer 或.der 檔案中的憑證指紋，附加 **/Thumbprint\<指紋\>** 命令。  
  
    這個工具會將憑證匯入 [憑證 (本機電腦)]\Other People\Certificates 存放區，並設定其組態。  
  
### <a name="to-import-a-root-key"></a>匯入根金鑰  
  
1. 按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2. 在命令提示字元中，移至[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]SDK 資料夾中的，使用 MS-DOS **CD**命令，例如，輸入**cd C:\Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK**。  
  
3. 在命令提示字元中，輸入**CertWizard /Rootkey\<檔名\>.cer**，其中\< *filename*\>.cer 包含根憑證。  
  
4. 如果您想要指定憑證的.cer 或.der 檔案中的憑證指紋，附加 **/Thumbprint\<指紋\>** 命令。  
  
    這個工具會將憑證匯入 [憑證 (本機電腦)]\Trusted Root Certification Authority\Certificates 存放區，並設定其組態。  
  
## <a name="see-also"></a>另請參閱  
 [CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)   
 [管理憑證](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)