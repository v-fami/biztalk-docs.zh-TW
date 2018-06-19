---
title: 預設管線 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines, XMLTransmit
- pipelines, StsReceive
- pipelines, StsSend
- pipelines, StsFileReceive
- Microsoft.BizTalk.KwTpm.StsDefaultPipelines.EnvSchema XML envelope
- pipelines, XMLReceive
- pipelines, backward compatibility
- Microsoft.BizTalk.DefaultPipelines assembly
- pipelines, default
ms.assetid: 7d82bb2c-c7f1-44a1-9e1b-89b0bb806845
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ceb3f06f2e2b57ec37bc4a95a385574de594940
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239302"
---
# <a name="default-pipelines"></a>預設管線
當您建立新的應用程式時，依照預設會建立和部署預設管線，並顯示在每個 BizTalk 專案的 \References 資料夾的 Microsoft.BizTalk.DefaultPipelines 組件中。 在「管線設計師」中不能修改預設管線。 在 [BizTalk 總管] 中設定傳送埠或接收位置時會選取這些管線。 本主題描述預設管線及其使用時機。  
  
> [!NOTE]
>  XML 接收和 XML 傳送管線不支援大於 4 GB 的 XML 文件。  
  
## <a name="passthrureceive-pipeline"></a>PassThruReceive 管線  
 通過接收管線沒有元件。 它用於不需要處理訊息內容的簡單通過實例。 此管線一般用在已知訊息來源和目的，且訊息不需驗證、編碼或解譯的時候。 此管線通常與通過傳送管線搭配使用。  
  
 因為通過接收管線不包含解譯器，所以不能用以路由訊息至協調流程。  
  
> [!NOTE]
>  通過接收管線不支援屬性升級。  
  
## <a name="passthrutransmit-pipeline"></a>PassThruTransmit 管線  
 通過傳送管線沒有元件。 此管線一般用在傳送訊息到目的之前不需要處理文件的時候。  
  
## <a name="xmlreceive-pipeline"></a>XMLReceive 管線  
 XML 接收管線包含下列階段：  
  
-   **解碼。** Empty  
  
-   **反組譯。** 包含 XML 解譯器元件  
  
-   **驗證。** Empty  
  
-   **解析合作對象。** 執行「合作對象解析」元件，將憑證主旨或來源安全性識別碼解析為合作對象識別碼。  
  
## <a name="xmltransmit-pipeline"></a>XMLTransmit 管線  
 XML 傳送管線包含下列階段：  
  
-   **預先組合。** Empty  
  
-   **組合。** 包含 XML 組合器元件  
  
-   **編碼。** Empty  
  
## <a name="see-also"></a>另請參閱  
 [類型的管線](../core/types-of-pipelines.md)   
 [類型的管線元件](../core/types-of-pipeline-components.md)   
 [管線範本](../core/pipeline-templates.md)   
 [管線元件](../core/pipeline-components.md)   
 [關於管線、 階段和元件](../core/about-pipelines-stages-and-components.md)