---
title: MIME SMIME 屬性結構描述和屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 26dd25b9-7eb8-4354-9929-dc1985dd1d77
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 882b25733a46b8b7b973c992d465132df4c47b75
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
ms.locfileid: "22263190"
---
# <a name="mime-smime-property-schema-and-properties"></a>MIME SMIME 屬性結構描述和屬性

## <a name="namespace-properties"></a>命名空間屬性
**http://schemas.microsoft.com/BizTalk/2003/mime-properties**命名空間包含可用來設定 MIME/SMIME 編碼器管線元件的訊息和部分內容屬性的屬性。 MIME/SMIME Encoder는 생성된 메시지에 적합한 MIME/SMIME 헤더를 생성하는 데 이러한 속성을 사용합니다. 다음 표는 MIME/SMIME 속성에 대해 설명합니다.  
  
|속성|범위|유형|Description|  
|--------------|-----------|----------|-----------------|  
|**檔名**|각 메시지 파트|xs:string|MIME/SMIME 파트의 파일 이름 헤더를 설정합니다.|  
|**ContentID**|각 메시지 파트|xs:string|MIME/SMIME 파트의 콘텐츠-ID 헤더를 설정합니다.|  
|**ContentDescription**|각 메시지 파트|xs:string|MIME/SMIME 파트의 콘텐츠-설명 헤더를 설정합니다.|  
|**ContentTransferEncoding**|각 메시지 파트|xs:string|생성된 MIME/SMIME 파트의 콘텐츠-전송-인코딩 헤더를 설정합니다.<br /><br /> 這個值會覆寫 **內容轉移編碼** 管線設計師 」 中所設定的值。 다중 파트 메시지의 경우 MIME/SMIME 파트마다 다른 인코딩을 사용할 수 있습니다.|  
|**ContentLocation**|각 메시지 파트|xs:string|생성된 MIME/SMIME 파트의 콘텐츠-위치 헤더를 설정합니다.|  
|**IsMIMEEncoded**|각 메시지 파트|xs:boolean|메시지에 MIME/SMIME 페이로드를 포함할지 여부를 지정합니다. MIME 구성 요소에서 이 값에 쓰므로 값을 설정할 필요가 없습니다.|  
  
 MIME/SMIME 編碼器也會使用下列部分屬性從 **系統** 命名空間。  
  
|속성|유형|Description|  
|--------------|----------|-----------------|  
|ContentType|xs:string|생성된 MIME/SMIME 파트의 콘텐츠-유형 헤더에 해당합니다.|  
|FileName|xs:string|파일 이름에 해당합니다.|  
  
## <a name="see-also"></a>另請參閱  
 [如何設定 MIME SMIME 解碼器管線元件](../core/how-to-configure-the-mime-smime-decoder-pipeline-component.md)   
 [如何設定 MIME SMIME 編碼器管線元件](../core/how-to-configure-the-mime-smime-encoder-pipeline-component.md)   
 [設定原生管線元件](../core/configuring-native-pipeline-components.md)   
 [MIME （BizTalk Server 範例）](../core/mime-biztalk-server-sample.md)   
 **訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]