---
title: 無法辨識的訊息，在 XML 組合器管線元件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XMLNorm.AllowUnrecognizedMessage property
- XML Assembler [pipeline component], unrecognized messages
- pipeline components, XML Assembler
ms.assetid: dd98512a-33a4-4b2e-977e-1b3a30747c6a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6766554374413c3d1b6a3ce385f24d4046521c91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286806"
---
# <a name="unrecognized-messages-in-the-xml-assembler-pipeline-component"></a>XML 組合器管線元件中無法辨識的訊息
如果訊息發生下列情況，則 XML 組合器元件會將訊息視為「無法辨識」：  
  
-   沒有內文部分。  
  
-   空的內文部分。  
  
-   內文部分中沒有資料。  
  
-   未部署相關聯的結構描述。  
  
> [!NOTE]
>  非 XML 訊息一律視為無法辨識。  
  
 XML 組合器處理無法辨識的訊息的方式由**XMLNorm.AllowUnrecognizedMessage**訊息內容屬性。  
  
 當**XMLNorm.AllowUnrecognizedMessage**設**True**，XML 組合器處理 XML 文件，如下所示：  
  
-   透過組合器並以原狀傳遞沒有內文部分或具有空白內容部分或空白資料的訊息。  
  
-   透過組合器並以原狀傳遞未部署與其相關聯之結構描述的文件。  
  
-   不論是在元件屬性中明確參考結構描述，或是在結構描述解析程序期間找到結構描述，都會透過組合器來處理具有相關聯之部署結構描述的文件。  
  
 如果**XMLNorm.AllowUnrecognizedMessage**設**False**，XML 組合器處理 XML 文件，如下所示：  
  
-   不會處理沒有內文部分或具有空白內容部分或空白資料的訊息。 會報告錯誤，並擱置訊息。  
  
-   不會處理未部署與其相關聯之結構描述的訊息。 會報告錯誤，並擱置訊息。  
  
-   不論是在元件屬性中明確參考結構描述，或是在結構描述解析程序期間找到結構描述，都會透過組合器來處理具有相關聯之部署結構描述的文件。  
  
-   根據預設，XML 組合器元件不允許無法辨識的訊息 (也就是**XMLNorm.AllowUnrecognizedMessages**會被視為**False**如果未設定在訊息內容)。  
  
## <a name="see-also"></a>另請參閱  
 [XML 組合器管線元件](../core/xml-assembler-pipeline-component.md)   
 [如何設定 XML 組合器管線元件](../core/how-to-configure-the-xml-assembler-pipeline-component.md)   
 [管線 AssemblerDisassembler （BizTalk Server 範例資料夾）](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)