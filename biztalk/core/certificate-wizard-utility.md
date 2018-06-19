---
title: 憑證精靈公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ff72810-c7b3-4f67-8f9f-e127eacc153e
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b0341a11c45cd08f8476d48ea38cbf96bcc49c1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26006175"
---
# <a name="certificate-wizard-utility"></a>憑證精靈公用程式
您可以使用 CertWizard 公用程式從.pfx 或.cer 檔案將憑證匯入到 Microsoft 搭配使用的私人或公用存放區[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
 憑證精靈的原始程式碼位於**C:\Program Files\Microsoft BizTalk Server\<版本\>\SDK\Utilities\Certificate 精靈**資料夾。 使用 64 位元作業系統與 BizTalk Server 的版本，它會處於**C:\Program Files (x86) \Microsoft BizTalk Server\<版本\>\SDK\Utilities\Certificate 精靈**資料夾。 若要使用 「 憑證精靈 」，您就必須先建立該使用 Visual Studio。  
  
 CertWizard 會從 .pfx file 檔案將私密金鑰匯入到個人存放區，從 .cer 檔案將公開金鑰匯入到公用存放區。 匯入私密金鑰時，可對內送訊息使用解密憑證，對外送訊息使用簽章憑證。  
  
 **語法描述**  
  
 下表描述 CertWizard 公用程式使用之語法的每個部分。  
  
|||  
|-|-|  
|語法|Description|  
|Privatekey|用來匯入私密金鑰。|  
|Publickey|用來匯入公開金鑰。|  
|Rootkey|用來匯入根金鑰—從憑證授權單位。|  
|filename.pfx (或 .cer)|.pfx (私密金鑰) 或 .cer (公開金鑰) 檔案的完整路徑。|  
|Filepassword|解除鎖定 .pfx 檔案所需的密碼。|  
|Useridentity|一或多個 BizTalk 主控件使用的服務識別。 如果您不想指定主控件，但想在使用者帳戶下匯入憑證，請輸入使用者帳戶。 **注意：** 如果您未加入 Useridentity 參數，此公用程式匯入，並針對所有使用者設定的憑證。 **注意：** 如果您加入 Useridentity 參數，但未輸入值，WMI 就會自動產生使用者識別。|  
|密碼|服務識別使用者的密碼。|  
|指模|特定憑證的指紋，以防檔案包含一個以上的憑證。 **注意：** 公開憑證檔案，如果該檔案包含一個以上的憑證，且您未指定指紋，此公用程式匯入檔案中的所有憑證。 對於私用憑證檔案，此公用程式會提示您選取要匯入的憑證。|  
|使用方式|匯入之私用憑證的用途。 可以是下列其中一項：<br /><br /> **符號**（適用於簽章的憑證）<br /><br /> **解密**（對於解密憑證）<br /><br /> **同時**（適用於憑證所簽署的憑證和解密憑證）<br /><br /> **無**（也適用於憑證所簽署的憑證和解密憑證）。 **注意：** 如果您將 /Usage 參數設為 none，精靈不會設定憑證的指紋 BizTalk 主控件或 BizTalk 群組上。|  
|Exportable|可以是**True**或**False**。 如果**True**，私密金鑰可以重複匯出。|  
  
 **匯入私用金鑰的語法**  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
 **匯入公開金鑰的語法**  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
 **匯入根金鑰的語法**  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
## <a name="prerequisites"></a>必要條件  
 下列是執行本主題所述程序的必要條件：  
  
-   您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-run-the-certificate-wizard"></a>若要執行憑證精靈  
  
1.  開啟命令提示字元。  
  
2.  移至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities。  
  
3.  在命令提示字元中，輸入**CertWizard**，輸入必要和適當的參數，然後按**Enter**。  
  
    > [!NOTE]
    >  如果您未在命令提示字元中提供完整的命令，CertWizard 會提示您輸入所需的值。  
  
## <a name="see-also"></a>請參閱  
 [SDK 中的公用程式](../core/utilities-in-the-sdk.md)