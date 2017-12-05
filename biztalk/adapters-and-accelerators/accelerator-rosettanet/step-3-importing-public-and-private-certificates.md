---
title: "步驟 3： 匯入公開憑證與私用憑證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public certificates
- importing certificates
- private certificates
- double action tutorial, importing certificates
- certificates, importing
ms.assetid: 955bdd69-9fbc-4100-ab8a-8f5dd4a17cbb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46d087c44cac350df2d58c880303668b5c3e0c24
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-importing-public-and-private-certificates"></a>步驟 3： 匯入公開憑證與私用憑證
在此步驟中，您匯入的憑證，您在建立[步驟 2： 建立公用和私用憑證 &#91;RN3 &#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) Contoso 和 Fabrikam 電腦。 每台電腦都會匯入自己的私用憑證，並匯入其他組織的公開憑證。  
  
> [!NOTE]
>  您必須將 Fabrikam 私用憑證和 Contoso 公開憑證傳送到 Fabrikam 電腦，才能匯入這些憑證。 此步驟假設您將這些憑證放置在 Fabrikam 電腦的 C:\Certs 資料夾內。  
  
### <a name="to-import-the-contoso-private-certificates-on-the-contoso-computer"></a>在 Contoso 電腦上匯入 Contoso 私用憑證  
  
1.  在 Contoso 電腦上，按一下 **啟動**，按一下 **執行**，型別**cmd**，然後按一下  **確定**。  
  
2.  在命令提示字元中，移至 **\<** *磁碟機***\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator forRosettaNet\SDK** ，然後按**Enter**。  
  
3.  在命令提示字元中，輸入**CertWizard /Privatekey"\<***磁碟機***\>: \Certs\Contoso Private Encryption.pfx"**，然後按下**輸入**。  
  
4.  在**請輸入憑證檔案的密碼**提示中，輸入**mysecret**，然後按下**Enter**。  
  
5.  在**輸入密碼的身分識別 < contoso_machine > \HostSvc**提示，輸入 HostSvc 帳戶密碼，然後按**Enter**。  
  
    > [!NOTE]
    >  如果使用 HostSvc 以外的帳戶名稱來執行 BizTalkServerApplication，提示將會不同。  
  
6.  在**此主要憑證將用於**提示中，輸入**D**，然後按下**Enter**。  
  
     CertWizard 會為執行 BizTalkServerApplication 及 BizTalkServerIsolatedHost 主控件的使用者帳戶，匯入憑證到 \Personal\Certificates 存放區。  
  
7.  重複步驟 3-6 Contoso Private Signature.pfx 憑證，指定它的簽章憑證是輸入**S**在**此主要憑證將用於**步驟 6 中的提示。  
  
### <a name="to-import-the-fabrikam-public-certificates-on-the-contoso-computer"></a>在 Contoso 電腦上匯入 Fabrikam 公開憑證  
  
1.  在 Contoso 電腦上，按一下 **啟動**，按一下 **執行，**類型**cmd**，然後按一下  **確定**。  
  
2.  在命令提示字元中，移至*\<磁碟機\>***: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK**然後按下**Enter**。  
  
3.  在命令提示字元中，輸入**CertWizard /Publickey"***\<磁碟機\>***: \Certs\Fabrikam Public Encryption.cer"**，然後按  **輸入**。  
  
4.  為 Fabrikam Public Signature.cer 憑證重複執行步驟 3。  
  
### <a name="to-import-the-fabrikam-private-certificates-on-the-fabrikam-computer"></a>在 Fabrikam 電腦上匯入 Fabrikam 私用憑證  
  
1.  將下列檔案複製至 Contoso 電腦\<磁碟機\>: Fabrikam 電腦上的 \Certs 資料夾： Contoso Public Encryption.cer、 Contoso Public Signature.cer、 Fabrikam Private Encryption.pfx 和 Fabrikam PrivateSignature.pfx。  
  
2.  按一下 Fabrikum 電腦上，按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
3.  在命令提示字元中，移至*\<磁碟機\>***: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK**然後按下**Enter**。  
  
4.  在命令提示字元中，輸入**CertWizard /Privatekey"***\<磁碟機\>***: \Certs\Fabrikam Private Encryption.pfx"**，然後按下**輸入**。  
  
5.  在**請輸入憑證檔案的密碼**提示中，輸入**mysecret**，然後按下**Enter**。  
  
6.  在**輸入密碼的身分識別 < fabrikam_machine > \HostSvc**提示，輸入 HostSvc 帳戶密碼，然後按**Enter**。  
  
    > [!NOTE]
    >  如果使用 HostSvc 以外的帳戶名稱來執行 BizTalkServerApplication，提示將會不同。  
  
7.  在**此主要憑證將用於**提示中，輸入**D**，然後按下**Enter**。  
  
     CertWizard 會為執行 BizTalkServerApplication 及 BizTalkServerIsolatedHost 主控件的使用者帳戶，匯入憑證到 \Personal\Certificates 存放區。  
  
8.  重複步驟 4-7，Fabrikam Private Signature.pfx 憑證，指定它的簽章憑證輸入**S**在**此主要憑證將用於**提示在步驟 6。  
  
### <a name="to-import-the-contoso-public-certificates-on-the-fabrikam-computer"></a>在 Fabrikam 電腦上匯入 Contoso 公開憑證  
  
1.  按一下 Fabrikum 電腦上，按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。  
  
2.  在命令提示字元中，移至*\<磁碟機\>***: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK**然後按下**Enter**。  
  
3.  在命令提示字元中，輸入**CertWizard /Publickey"***\<磁碟機\>***: \Certs\Contoso Public Encryption.cer"**，然後按  **輸入**。  
  
4.  為 Contoso Public Signature.cer 憑證重複執行步驟 3。  
  
## <a name="see-also"></a>請參閱  
 [步驟 4：在 IIS 中啟用安全通訊端層 (SSL)](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)