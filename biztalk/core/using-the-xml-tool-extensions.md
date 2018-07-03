---
title: 使用 XML 工具延伸模組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5613bf15-6c0a-4a82-b200-24d0801d7ece
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8628ffdbbb2844c7ce8afff3dfe903d0723449
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36992487"
---
# <a name="using-the-xml-tool-extensions"></a>使用 XML 工具延伸模組
XML 工具延伸模組，以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您在結構描述、 對應、 執行工作和訊息執行個體。 您可以在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 環境中的設計階段使用這些延伸模組。 您可以執行的工作如下：  
  
- **驗證結構描述**。 這項作業會根據 EDI 規則來驗證 EDI 結構描述。 如需詳細資訊，請參閱 <<c0> [ 驗證結構描述 (EDI)](../core/validating-a-schema-edi.md)。  
  
- **驗證訊息執行個體**。 這項作業會驗證單一交易集 (不含交換和群組標頭) 或包含多個交易集的完整批次交換 (含交換和群組標頭)。 若要驗證非批次交換，您必須將交換和群組標頭從執行個體移除。 如需詳細資訊，請參閱 <<c0> [ 驗證的執行個體 (EDI)](../core/validating-an-instance-edi.md)。  
  
- **產生訊息執行個體**。 這項作業會產生完整的批次交換或不含交換和群組標頭的交易集。 您必須指定分隔符號、識別碼和其他用來產生執行個體的格式設定。 如需詳細資訊，請參閱 <<c0> [ 產生的執行個體 (EDI)](../core/generating-an-instance-edi.md)。  
  
- **測試對應**。 這項作業會根據來源文件和對應產生輸出文件 (包含虛構資料)。 如需詳細資訊，請參閱 <<c0> [ 測試對應](../core/testing-a-map.md)。  
  
- **驗證對應**。 這項作業會產生兩個檔案：一個檔案包含對應的基礎 XSLT，一個檔案包含延伸模組物件。 如需詳細資訊，請參閱 <<c0> [ 驗證對應 (EDI)](../core/validating-a-map-edi.md)。  
  
  在 BizTalk Server 中，這些延伸模組可處理 EDI 結構描述、 對應和訊息執行個體。 這些延伸模組可讓您更有效率地處理複雜的 EDI 結構描述、對應和交換。  
  
  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝程式預設會啟用 XML 工具延伸模組。 如果您按兩下在 Visual Studio 的方案總管中的結構描述**Schema Editor Extensions**結構描述的屬性設定為**EDI 結構描述編輯器延伸模組**。 如此 XML 工具延伸模組才能運作。 您可以在保留選取 EDI 延伸模組的同時，選取其他結構描述編輯器延伸模組。  
  
## <a name="see-also"></a>另請參閱  
 [產生執行個體 (EDI)](../core/generating-an-instance-edi.md)   
 [驗證執行個體 (EDI)](../core/validating-an-instance-edi.md)   
 [驗證結構描述 (EDI)](../core/validating-a-schema-edi.md)   
 [測試對應](../core/testing-a-map.md)   
 [驗證對應 (EDI)](../core/validating-a-map-edi.md)