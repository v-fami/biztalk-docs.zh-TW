---
title: "如何設定 MIME SMIME 編碼器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, encrypting digital signatures
- pipeline components, MIME/SMIME Encoder
- Partner Management, security
- MIME/SMIME Encoder [pipeline component], configuring
- messages, encoding
- messages, multi-parts
ms.assetid: dcbb08e8-d300-4e7f-9c1c-907fb602e721
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07cabef8510fb2189da759ba9b0c156ef672410e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-mime-smime-encoder-pipeline-component"></a>如何設定 MIME SMIME 編碼器管線元件
使用 MIME/SMIME 編碼器元件可編碼和解碼外寄訊息，並簽章外寄訊息。 當您要求在 BizTalk Server 與外部夥伴之間進行安全文件交換時，這個元件十分有用。 您也可以使用此元件來傳送 BizTalk Server 多部分訊息。  
  
> [!NOTE]
>  在 BizTalk 2006 中，MIME/SMIME 編碼器管線元件將不再具有原生 64 位元支援。  這表示，此元件必須在 32 位元模擬模式程序 (WOW64) 中執行。  而這也暗示，在其中執行此編碼器元件的主控件執行個體 (或此元件為其一部分的傳送管線)，必須以 32 位元模擬模式執行。  請注意，這項限制對於在此相同主控件執行個體中執行的其他 BizTalk 項目，也會有效能上 (或其他方面) 的暗示。  
  
### <a name="to-configure-the-properties-for-the-mimesmime-encoder-pipeline-component"></a>設定 MIME/SMIME 編碼器管線元件的屬性  
  
1.  將 MIME/SMIME 編碼器管線元件拖曳至接收管線的編碼階段中。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**新增至訊息的簽章憑證**|如果**簽章類型**屬性不是**NoSign**，您可以選擇是否要加入簽章的訊息中的簽章憑證，藉由設定**Add Signing Cert to 訊息**屬性。<br /><br /> 預設值： **，則為 True**|  
    |**檢查撤銷清單**|指定在處理 SMIME 訊息時，是否檢查憑證撤銷清單。<br /><br /> 預設值： **，則為 True**|  
    |**內容轉移編碼**|指出編碼格式。<br /><br /> 選項：Base64、QuotedPrintable、SevenBit、EightBit、Binary 和 UUEncode。<br /><br /> 預設值： **Base64**|  
    |**啟用加密**|設定為**True**如果您想要加密外寄訊息。 如果啟用此選項時，使用者可以選取要藉由設定使用的加密演算法**加密演算法**屬性。 針對訊息加密，MIME/SMIME 編碼器管線元件會使用與 BizTalk 總管相關聯的公開金鑰憑證。<br /><br /> 預設值： **False**|  
    |**加密演算法**|定義加密演算法。<br /><br /> 這個屬性只能設定，如果**啟用加密**設**True**。<br /><br />**從開始[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]和較新版本**，會自動包含的 AES 加密。 選項包括： DES3、 DES、 RC2、 AES128 （預設）、 AES192 和 AES256。<br /><br />如先前[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]版本中，選項包括： DES3 （預設）、 DES、 RC2。|  
    |**以附件傳送內文部分**|設定為**True**如果您想要以 MIME 附件傳送 BizTalk 訊息內文合作對象。<br /><br /> 預設值： **False** **重要事項：**不應該將此屬性設**True**時 BizTalk 伺服器之間傳送的訊息。 否則，因為在接收端會將訊息解譯為兩部分訊息，所以訊息解密將會要求自訂編碼。|  
    |**簽章類型**|如果您想要簽章外寄訊息，請選取使用此屬性的簽章格式。 此屬性具有三個值：<br /><br /> -   **NoSign**。 不會簽章訊息。<br />-   **ClearSign**。 簽章將會附加到訊息。 **ClearSign**如果無法使用**啟用加密**設**True**。<br />-   **BlobSign**。 簽章將會附加到訊息，而且會編碼訊息。<br /><br /> 針對訊息簽章，MIME/SMIME 編碼器元件會使用與 [BizTalk 管理] 主控台中之 [BizTalk 群組] 相關聯的私密金鑰用戶端憑證。<br /><br /> 預設值： **NoSign**|  
  
 若要設定 MIME 附件的檔案名稱，使用**FileName**屬性**系統**訊息部分的命名空間。  
  
## <a name="see-also"></a>另請參閱  
 [MIME SMIME 編碼器管線元件](../core/mime-smime-encoder-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md)   
 [MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)