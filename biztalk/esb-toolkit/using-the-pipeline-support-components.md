---
title: "使用管線支援元件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: df0346ea-15d4-49c5-98d8-f9ec06f4e036
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6313a337e8527f3fb275f7c15745a5a7f6552151
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-pipeline-support-components"></a>使用管線支援元件
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含下列管線元件：  
  
-   **ESB 路線選取器**。 您可以使用此元件在接收端 （在接收管線），以選取要遵循的訊息伺服器端路線。 如需詳細資訊，請參閱[ESB 行程選取器元件](../esb-toolkit/the-esb-itinerary-selector-component.md)。  
  
-   **ESB 行程**。 您可以使用此元件在接收端 （在接收管線），若要將 SOAP 標頭 ESB 中繼資料屬性升級為訊息內容。 如需詳細資訊，請參閱[ESB 行程元件](../esb-toolkit/the-esb-itinerary-component.md)。  
  
-   **ESB 路線轉寄站**。 如需詳細資訊，請參閱[ESB 行程轉寄站元件](../esb-toolkit/the-esb-itinerary-forwarder-component.md)。  
  
-   **ESB 路線快取**。 您可以使用此元件，將快取旅，並套用到接收的請求-回應傳送埠的回應訊息。 如需詳細資訊，請參閱[ESB 行程元件](../esb-toolkit/the-esb-itinerary-component.md)。  
  
-   **ESB JMS 解碼器**。 您可以使用此元件在接收端 （在接收位置） 的協調流程或傳送埠，來剖析出 IBM JMS (MQRFH2) 標頭，並保留這些內容屬性。 您可以存取這些內容屬性，並在任何其他 BizTalk 內容屬性的相同方式來修改它們。 如需詳細資訊，請參閱[ESB JMS 編碼器和解碼器元件](../esb-toolkit/the-esb-jms-encoder-and-decoder-components.md)。  
  
-   **ESB JMS 編碼器**。 您可以使用傳送埠中的此元件將 IBM JMS (MQRFH2) 標頭寫入訊息。 如需詳細資訊，請參閱[ESB JMS 編碼器和解碼器元件](../esb-toolkit/the-esb-jms-encoder-and-decoder-components.md)。  
  
-   **ESB 加入命名空間**。 您可以使用 接收位置或傳送埠的此元件將 XML 文件中加入命名空間。 如需詳細資訊，請參閱[ESB 加入命名空間及移除命名空間元件](../esb-toolkit/the-esb-add-namespace-and-remove-namespace-components.md)。  
  
-   **ESB 移除命名空間**。 若要移除 XML 文件中的命名空間，您可以使用此接收位置或傳送埠中的元件。 如需詳細資訊，請參閱[ESB 加入命名空間及移除命名空間元件](../esb-toolkit/the-esb-add-namespace-and-remove-namespace-components.md)。  
  
-   **ESB 例外狀況的編碼器**。 您可以使用此元件將錯誤訊息傳送至檔案系統中，Microsoft InfoPath 或 Microsoft SharePoint。 這個元件是 ESB 例外狀況處理機制的一部分，標準化並充實所有傳送埠所處理的例外狀況。 元件序列化例外狀況資訊 （包括內嵌保存的訊息和內容屬性） 標準格式，讓所有包含訊息本身的例外狀況而提供。  
  
-   **ESB 轉換**。 您可以使用此元件，藉由指定 BizTalk 對應轉換到另一種格式的訊息。  
  
-   **ESB BAM 追蹤器**。 您可以使用此元件以攔截 ESB 例外狀況編碼器所發出的錯誤訊息，並在訊息中的資料插入 BAM 主要匯入資料表 （使用管線中的 BAM 事件資料流）。 這個元件是 ESB 例外狀況處理機制的一部分。  
  
-   **ESB 發送器**。 您可以使用此元件在接收位置 （輸入管線），來動態設定輸出訊息的端點位置屬性。 您也可以在傳送管線中使用這個元件執行路線訊息的服務。 如需詳細資訊，請參閱[ESB 發送器元件](../esb-toolkit/the-esb-dispatcher-component.md)。  
  
-   **ESB 發送器反組譯**。 您可以使用此元件在接收位置 （輸入管線），來動態設定輸出訊息的端點位置屬性。 此元件的行為是 ESB 發送器元件，類似，不同之處在於它會將轉換的結果訊息 (如果您指定的值**MapName**屬性)。 訊息通過 「 XML 解譯器 」，將提升的屬性和訊息類型。 ESB 發送器解譯元件也支援批次的分派到不同的端點的多個訊息。 如需詳細資訊，請參閱[ESB 發送器解譯元件](../esb-toolkit/the-esb-dispatcher-disassemble-component.md)。