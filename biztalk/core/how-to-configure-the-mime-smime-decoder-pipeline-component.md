---
title: "如何設定 MIME SMIME 解碼器管線元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, attachments
- pipeline components, MIME/SMIME Decoder
- MIME/SMIME Decoder [pipeline component], configuring
- messages, verifying
- messages, decoding
- messages, digital signatures
- messages, security
ms.assetid: bfd44893-f1c3-4524-abc6-f820b8c0ef07
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a32137528de5ea18ea5698ab823c2e703651b71b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-mime-smime-decoder-pipeline-component"></a>如何設定 MIME SMIME 解碼器管線元件
MIME/SMIME 解碼器管線元件可用來解碼和解密經過 MIME/SMIME 編碼的訊息，也可以用來驗證簽章訊息的數位簽章。 當外部夥伴和 BizTalk Server 之間需要安全的文件交換時，這個元件會非常有用。 在接收有附件的訊息時也可以使用這個元件。  
  
> [!NOTE]
>  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，MIME/SMIME 解碼器管線元件並沒有原生 64 位元支援。  這表示，此元件必須在 32 位元模擬模式程序 (WOW64) 中執行。  而這也暗示，此解碼器元件執行所在的主控件執行個體 (或此元件所在的接收管線)，必須以 32 位元模擬模式執行。  請注意，這項限制對於在此相同主控件執行個體中執行的其他 BizTalk 項目，也會有效能上 (或其他方面) 的暗示。  
  
> [!NOTE]
>  MIME/SMIME 解碼器元件也用於 POP3 配接器。  因此，相同的原生 64 位元支援限制也存在於 POP3 配接器執行所在的主控件執行個體中。  請參閱中的 POP3 配接器的相關的資訊[POP3 配接器](../core/pop3-adapter.md)。  
  
### <a name="to-configure-the-properties-for-the-mimesmime-decoder-pipeline-component"></a>設定 MIME/SMIME 解碼器管線元件的屬性  
  
1.  將 MIME/SMIME 解碼器管線元件拖曳至接收管線的「解碼」階段中。  
  
2.  在 [屬性] 視窗中**管線元件屬性**區段中，執行下列動作。  
  
    |使用|動作|  
    |--------------|----------------|  
    |**允許非 MIME 訊息**|將此屬性設定為**True**如果您預期接收管線可能會收到不 MIME 編碼的訊息。 當 MIME/SMIME 解碼器元件用於接收不同格式訊息 (例如，以 MIME 編碼或標準 XML) 時，此選項很實用。 根據預設，這個屬性設定為**False**，如果它接收到非 MIME 元件會產生錯誤的意義編碼的輸入訊息時。 **注意：** MIME 解碼器會掃描傳入訊息來搜尋 「 MIME 版本 」 標頭前 1024 個位元組。 若沒找到此標頭，則此訊息將被視為非 MIME 訊息。 <br /><br /> 預設值： **False**|  
    |**內文部分內容類型**|指示 MIME 部分的內容類型。 具有此內容類型的 MIME 部分將會變成 BizTalk 訊息的內文部分。<br /><br /> 預設值：無|  
    |**內文部分索引**|指示一維索引成為 MIME 部分清單。 在清單中此索引上的 MIME 部分將會變成 BizTalk 訊息的內文部分。 若要停用索引的內文部分選取項目，請使用值**0**。<br /><br /> 預設值： **0**|  
    |**檢查撤銷清單**|將此屬性設定為**True**如果您想要檢查憑證撤銷清單，傳送者用來簽署傳送至 BizTalk Server 訊息的憑證。 停用此選項會提高元件的效能。<br /><br /> 與憑證相關聯的憑證撤銷清單可從遠端網站下載的 (例如，Verisign.com)。 若 BizTalk Server 無法連結至遠端網站，則訊息將在管線中發生失敗。<br /><br /> 預設值： **，則為 True**|  
  
## <a name="see-also"></a>另請參閱  
 [MIME SMIME 解碼器管線元件](../core/mime-smime-decoder-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md)   
 [MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)