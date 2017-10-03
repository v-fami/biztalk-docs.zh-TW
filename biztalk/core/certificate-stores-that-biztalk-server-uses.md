---
title: "BizTalk Server 使用的憑證存放區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public key certificates
- certificate stores, warnings
- private key certificates
- certificates, private key
- Other People stores [certificates]
- certificate stores, Personal store
- Personal store [certificates]
- certificate stores, Windows stores
- certificates, public key
- certificates, certificate stores
- certificate stores
ms.assetid: 29b65913-be3b-45d9-9865-02e52e4370f4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b142ff5b9c9007a86b09acd25f53f8c88796988c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-stores-that-biztalk-server-uses"></a>BizTalk Server 使用的憑證存放區
BizTalk Server 使用兩種憑證存放區：公開金鑰的「其他人」憑證存放區，以及私密金鑰的每個主控件執行個體服務帳戶的「個人」憑證存放區。  
  
 **其他人 」 憑證存放區中。** 正如其名所指，公開金鑰憑證即是公開可供任何人存取的憑證，但是此人必須有權存取儲存該憑證的電腦。 BizTalk Server 使用公開金鑰憑證來加密要送至特定合作對象的訊息，並驗證來自特定合作對象的內送訊息的數位簽章。 Windows 提供「其他人」憑證存放區來儲存電腦上使用的公開金鑰憑證。 所有的使用者都可以讀取及使用這個存放區內的憑證，而 Windows 系統管理員具有維護此存放區的權限。  
  
> [!NOTE]
>  您必須將公開金鑰憑證儲存在本機電腦的「本機電腦\其他人」憑證存放區，而這台電腦中會有 BizTalk 主控件執行個體，可用來驗證簽章或加密傳送至遠端夥伴的訊息。  
  
 下圖顯示 BizTalk Server 針對公開金鑰憑證所使用的「其他人」憑證存放區：  
  
 ![其他人 」 憑證存放區](../core/media/bpi-sp-msgsec-otherpeoplecertstore.gif "BPI_SP_MSGSEC_OTHERPEOPLECERTSTORE")  
  
 **個人憑證存放區。** BizTalk Server 使用私密金鑰憑證來解密內送訊息及簽署輸出訊息。 在電腦上用來進行互動式登入的每個 Windows 帳戶都會有作業系統所儲存僅供該帳戶存取的個人憑證存放區。 BizTalk Server 使用各主控件執行個體服務帳戶的個人憑證存放區來存取每個服務帳戶有權存取的私密金鑰憑證。 只有憑證存放區的擁有者才可以存取及維護各自的個人憑證存放區。 也就是說，您必須以各主控件服務帳戶登入每一台裝載 S/MIME 解碼管線的電腦，然後使用 [憑證] 嵌入式管理單元，將解密憑證匯入至個人憑證存放區。  
  
 下圖顯示 BizTalk Server 針對私密金鑰憑證所使用的「個人」憑證存放區：  
  
 ![目前的使用者憑證存放區](../core/media/bpi-sp-msgsec-mystore.gif "BPI_SP_MSGSEC_MYSTORE")  
  
> [!IMPORTANT]
>  私密金鑰憑證必須已經儲存在每一台電腦上各個主控件執行個體服務帳戶的「目前使用者\個人」憑證存放區，而這些電腦中存在的 BizTalk (執行中的主控件執行個體) 需要可用來解密或簽署輸出訊息的憑證。  
  
> [!NOTE]
>  在新增用來簽署輸出訊息的私密金鑰憑證到服務帳戶的個人憑證存放區之後，您也必須在 BizTalk 管理主控台中指定這個簽章憑證。 如需詳細資訊，請參閱[傳送簽署的訊息設定 BizTalk Server 如何](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)。  
  
> [!NOTE]
>  當用於程式設計作業 (如憑證匯入及匯出的指令碼處理) 時，個人憑證存放區也稱為 MY 憑證存放區。  
  
 下表說明必須在每個 Windows 憑證存放區中安裝的憑證。  
  
### <a name="table-1-certificates-for-each-windows-certificate-store"></a>表 1：每個 Windows 憑證存放區的憑證  
  
|**憑證用途**|**憑證類型**|**憑證存放區**|  
|-----------------------------|--------------------------|---------------------------|  
|簽署|自有私密金鑰|每個服務帳戶具有傳送管線，其設定來簽署訊息的 MIME/SMIME 編碼器管線元件的主控件執行個體的個人存放區 (**加入簽章憑證至訊息**屬性設定為`True`)。 如需詳細資訊，請參閱[如何設定 BizTalk Server 傳送簽署的訊息](../core/how-to-configure-biztalk-server-for-sending-signed-messages.md)|  
|驗證簽章|夥伴的公開金鑰|具有主控件執行個體的各台電腦上的「其他人」存放區；這個執行個體具有包含 MIME/SMIME 解碼器管線元件的接收管線。 如需詳細資訊，請參閱[如何設定接收簽署訊息的 BizTalk 伺服器](../core/how-to-configure-biztalk-server-for-receiving-signed-messages.md)。|  
|解密|自有私密金鑰|主控件執行個體的各個服務帳戶的個人存放區；這個執行個體具有包含 MIME/SMIME 解碼器管線元件的接收管線。 如需詳細資訊，請參閱[如何設定 BizTalk Server 接收加密訊息](../core/how-to-configure-biztalk-server-for-receiving-encrypted-messages.md)。|  
|加密|夥伴的公開金鑰|其他人 」 存放區已具有傳送管線，其設定為用於加密訊息的 MIME/SMIME 編碼器管線元件的主控件執行個體的每部電腦上 (**啟用加密**屬性設定為`True)`。 如需詳細資訊，請參閱[如何設定 BizTalk Server 傳送加密訊息](../core/how-to-configure-biztalk-server-for-sending-encrypted-messages.md)。|  
|合作對象解析|夥伴的公開金鑰|在管理電腦上的「其他人」存放區，您將會從此存放區中設定合作對象解析。 如需詳細資訊，請參閱[使用憑證進行合作對象解析](../core/using-certificates-for-party-resolution.md)。|  
  
 下圖顯示您在接收訊息專用的 BizTalk Server 上的每個憑證存放區中，將會需要哪些憑證。  
  
 ![接收安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-receive.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Receive")  
  
 下圖顯示您在傳送訊息專用的 BizTalk Server 上的每個憑證存放區中，將會需要哪些憑證。  
  
 ![傳送安全訊息所需的憑證](../core/media/bpi-sp-msgsec-certmgmt-certstores-send.gif "BPI_SP_MSGSEC_CertMgmt_CertStores_Send")  
  
 如需有關 Microsoft 管理主控台 (MMC) 之憑證存放區和 [憑證] 嵌入式管理單元的詳細資訊，請在「Windows 說明」中搜尋＜憑證主控台＞。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 用於簽章訊息的憑證](../core/certificates-that-biztalk-server-uses-for-signed-messages.md)   
 [BizTalk Server 會使用加密訊息的憑證](../core/certificates-that-biztalk-server-uses-for-encrypted-messages.md)   
 [加密和簽章憑證](../core/encryption-and-signing-certificates.md)   
 [實作訊息安全性](../core/implementing-message-security.md)