---
title: MIME SMIME 編碼器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipeline components, MIME/SMIME Encoder
- MIME/SMIME Encoder [pipeline component]
- BTS.EncryptionCert property
ms.assetid: 397505e6-47d0-4b63-9197-814ee4388369
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6c6a79052d3294420c46bff2a1ce3c0ed869e48
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263062"
---
# <a name="mime-smime-encoder-pipeline-component"></a>MIME SMIME 編碼器管線元件
MIME/SMIME 編碼器元件可以放置在傳送管線的編碼階段中。 它支援 7 位元、8 位元、二進位、quoted-printable、base64 以及 UUencode 編碼。 當地語系化資料字元集變更不會影響編碼。  
  
 此元件可用以進行 MIME 編碼，使用加密與簽章憑證以簽署或加密外寄訊息。  
  
 若傳送管線中具有設定為簽署訊息的編碼元件，而包含執行管線之主控件的 BizTalk 群組未設定使用簽章憑證，則外寄訊息將被擱置 (發出錯誤訊息) 到執行管線之主控件的擱置佇列中。 若在執行服務下的目前使用者之個人憑證存放區中找不到簽章憑證，則訊息將擱置到執行管線之主控件的擱置佇列中。  
  
 若輸出管線中的編碼元件設定為加密輸出訊息，而在憑證存放區中找不到憑證，則訊息將擱置到執行管線之主控件的擱置佇列中。  
  
 若要在接收已簽章和已加密訊息的要求-回應連接埠上執行回應加密，則自訂管線元件必須在 MIME/SMIME 編碼器管線元件之前加入管線。 此自訂管線元件必須識別對應至加密憑證的指紋，並且將它設定為**BTS。EncryptionCert**在訊息內容屬性。 如需訊息內容屬性的詳細資訊，請參閱[如何修改群組內容](../core/how-to-modify-group-properties.md)。  
  
 如需設定 MIME/SMIME 編碼器管線元件的資訊，請參閱[如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)。 如需 BizTalk Server 支援加密、 簽署及憑證的使用方式的詳細資訊，請參閱[傳送和接收訊息的安全性](../core/security-for-sending-and-receiving-messages.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管線元件](../core/pipeline-components.md)   
 [MIME SMIME 屬性結構描述和屬性](../core/mime-smime-property-schema-and-properties.md)   
 [MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)