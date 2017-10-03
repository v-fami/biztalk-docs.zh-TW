---
title: "CertWizard |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, CertWizard utility
- CertWizard utility
- certificates, importing
ms.assetid: beeab3c0-d7b1-4bb9-8b19-f79b049d5aa1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8d9daf4ea1ea996680088c7a7a1333e9d26906b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="certwizard"></a>CertWizard
您可使用 CertWizard 公用程式從 .pfx 或 .cer 檔案將憑證匯入到私用或公用存放區，以搭配 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 使用。  
  
## <a name="location-in-sdk"></a>SDK 中的位置  
 \<*磁碟機*> \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\  
  
## <a name="running-certwizard"></a>執行 CertWizard  
  
#### <a name="to-run-certwizard"></a>若要執行 CertWizard  
  
1.  開啟命令提示字元。  
  
2.  移至\<*磁碟機*> \ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for RosettaNet\SDK\\。  
  
3.  在命令提示字元中，輸入**CertWizard**，輸入必要和適當的參數，然後按 ENTER 鍵。  
  
## <a name="syntax-for-certwizard"></a>CertWizard 的語法  
 以下顯示您可用來啟動此命令列公用程式的語法：  
  
### <a name="syntax-for-importing-a-private-key"></a>匯入私密金鑰的語法  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
### <a name="syntax-for-importing-a-public-key"></a>匯入公開金鑰的語法  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-for-importing-a-root-key"></a>匯入根金鑰的語法  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-description"></a>語法描述  
 下表描述 CertWizard 公用程式使用之語法的每個部分。  
  
|**語法**|**說明**|  
|----------------|---------------------|  
|**Privatekey**|用來匯入私密金鑰。|  
|**Publickey**|用來匯入公開金鑰。|  
|**Rootkey**|用來匯入根金鑰—從憑證授權單位。|  
|**filename.pfx （或.cer）**|.pfx (私密金鑰) 或 .cer (公開金鑰) 檔案的完整路徑。|  
|**Filepassword**|解除鎖定 .pfx 檔案所需的密碼。|  
|**Useridentity**|一或多個 BizTalk 主控件使用的服務識別。 如果您不想指定主控件，但想在使用者帳戶下匯入憑證，請輸入使用者帳戶。 **注意：**如果您需要新增**Useridentity**切換，公用程式匯入，並針對所有使用者設定的憑證。 **注意：**如果您將加入**Useridentity**參數，但未輸入值，WMI 會自動產生使用者識別。|  
|**密碼**|服務識別使用者的密碼。|  
|**憑證指紋**|特定憑證的指紋，以防檔案包含一個以上的憑證。 **注意：**公開憑證檔案，如果該檔案包含一個以上的憑證，且您未指定指紋，此公用程式匯入檔案中的所有憑證。 對於私用憑證檔案，此公用程式會提示您選取要匯入的憑證。|  
|**使用方式**|匯入之私用憑證的用途。 可為 sign (對於簽章憑證)、decrypt (對於解密憑證)、both (對於同時是簽章憑證又是解密憑證的憑證)，或 none (也是對於同時是簽章憑證又是解密憑證的憑證)。 **注意：**如果您設定**/Usage**參數設為 none，精靈就不在的 BizTalk 主控件或 BizTalk 群組上設定憑證的指紋。|  
|**可匯出**|它可以是 `True` 或 `False`。 如果是 `True`，私密金鑰可能會再匯出一次。|  
  
## <a name="remarks"></a>備註  
 CertWizard 會從 .pfx file 檔案將私密金鑰匯入到個人存放區，從 .cer 檔案將公開金鑰匯入到公用存放區。 匯入私密金鑰時，可對內送訊息使用解密憑證，對外送訊息使用簽章憑證。  
  
 如果您未在命令提示字元中提供完整的命令，CertWizard 會提示您輸入所需的值。  
  
## <a name="see-also"></a>另請參閱  
 [公用程式](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md)   
 [使用 CertWizard 公用程式匯入憑證](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)