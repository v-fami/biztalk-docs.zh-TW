---
title: 測試結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c2e28b7c-9d0c-4336-8bee-4599d41a57f4
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc036be84bb64e794e6109e1ebc4ec730f382878
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023108"
---
# <a name="testing-schemas"></a>測試結構描述
建立結構描述之後，您可能會想要驗證它是否描述您想要它描述的 XML 結構。 您可在您的結構描述上執行下列三種作業來進行驗證：  
  
- **執行個體產生**。 此作業會從結構描述產生執行個體訊息、建立要伴隨結構描述所指定之 XML 項目和屬性的測試資料。  
  
- **結構描述驗證**。 此作業會驗證結構描述的內部一致性，確保它符合「XML 結構描述定義」(XSD) 語言結構描述標準。  
  
- **執行個體驗證**。 此作業會依據結構描述，驗證指定的執行個體訊息。  
  
  在將您的結構描述應用於生產環境之前，使用這三種作業先進行測試會很有用。  
  
  本節將詳細描述這些作業。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何驗證在 Visual Studio 中的結構描述](../core/how-to-validate-schemas-in-visual-studio.md)  
  
-   [如何驗證執行個體訊息](../core/how-to-validate-instance-messages.md)  
  
-   [如何產生執行個體訊息](../core/how-to-generate-instance-messages.md)