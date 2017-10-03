---
title: "如何將協調流程對應至 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, Web services
- BizTalk Web Services Publishing Wizard, naming conventions
- Web services, orchestrations
- orchestrations, naming conventions
- Web services, naming conventions
ms.assetid: e6a58978-c81c-49f3-9428-9bff60f1ded7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f101a9a9ab6c0d99e9895433401de08b1380d1e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-orchestrations-to-web-services"></a>如何將協調流程對應至 Web 服務
一個協調流程可以具有多個接收埠。 使用 [BizTalk Web 服務發佈精靈]，即可選取要發佈為 Web 服務的接收埠。 此精靈可為每個接收埠建立一個 Web 服務 (.asmx 檔案)。 如果所有的接收埠都屬於相同的接收埠類型 (「單向」或「要求/回應」)，此精靈也可為所有的接收埠建立單一的 Web 服務。 作業變成函式呼叫。 接收埠中的每個作業都會變成 Web 方法。 要求作業變成輸入參數。 回應作業變成傳回型別。  
  
 如果要求和回應的作業相同的 Web 訊息類型，輸入的參數就會變成**ref**和傳回型別是**void**。 ASP.NET Web 用戶端可能會合併相同型別的 in 和 out 參數，以變更 Web 方法簽章。 例如，ASP.NET Web 用戶端可能會變更 BizTalk Web 方法，從**string myService （字串一部分）**至**void myService （ref 字串的一部分）**。  
  
 作業訊息類型可定義 Web 方法簽章。 每個訊息類型部分都是 Web 方法中的參數。  
  
## <a name="message-type-part-names-and-target-namespaces"></a>訊息類型部分名稱和目標命名空間  
 文件結構描述和使用者定義類別**XmlRootAttribute**指定是訊息類型部分定義目標命名空間。 EDI 結構描述、 使用者定義的類別，而不**XmlRootAttribute**指定和內建類型，例如**System.String**是未定義的目標命名空間的訊息類型部分。  
  
|如果訊息類型部分名稱有|使用的參數名稱|  
|-----------------------------------------|-------------------------|  
|定義的目標命名空間|根項目名稱|  
|沒有定義的目標命名空間|訊息類型部分名稱|  
  
> [!NOTE]
>  在回應訊息使用 multipart 訊息類型時，[BizTalk Web 服務發佈精靈] 會使用第一個訊息部分做為傳回值，並會使用其餘的訊息部分做為 out 參數。  
  
## <a name="orchestrations-with-multiple-operations"></a>具有多重作業的協調流程  
 如果您的協調流程具有多重作業，此協調流程應該設計為使用一個接收埠，而非多個接收埠。 這種設計可防止「BizTalk Web 服務發佈精靈」建立多個 Web 服務 (.asmx) 檔案，而只在所有的作業都具有相同的呼叫模式 (全都是單向作業，或者全都是要求-回應作業) 情況下運作。 單一的接收埠不能同時包含單向和要求/回應作業。  
  
> [!NOTE]
>  [BizTalk Web 服務發佈精靈] 會顯示公用的接收埠。 公用的接收埠屬於具有公用型別修飾詞的連接埠類型。 您只能將公用連接埠發佈為 Web 服務。 預設的連接埠類型為「內部」。  
  
> [!NOTE]
>  如果您收到定義為單向連接埠、 Web 方法回應型別是**void**和 Web 用戶端傳回任何資訊。 SOAP 配接器或協調流程所擲回的例外狀況，都不會傳回到 Web 用戶端。  
  
## <a name="web-services-naming-conventions-for-published-orchestrations"></a>已發佈協調流程的 Web 服務命名慣例  
 BizTalk Web 服務發佈精靈產生 Web 服務 (.asmx) 檔案名稱，而根據協調流程命名空間，後面接著底線 (_)，後面接著類型名稱，後面接著底線 (\_)，後面接著接收名稱和連接埠。 底線 (\_) 會取代任何包含句號的組件。 Web 服務的名稱永遠都會加上該連接埠名稱。  
  
 下表顯示「BizTalk Web 服務發佈精靈」如何產生 Web 服務名稱。  
  
|協調流程與 Web 連接埠|產生的 Web 服務名稱|  
|-------------------------------------------|--------------------------------|  
|具有一個 Web 連接埠的一個協調流程|orchestration1_port1.asmx|  
|具有兩個 Web 連接埠的一個協調流程|orchestration1_port1.asmx 和 orchestration1_port2.asmx|  
|各有一個 Web 連接埠的兩個協調流程|orchestration1_port1.asmx 和 orchestration2_port2.asmx|  
  
## <a name="see-also"></a>另請參閱  
 [協調流程發佈為 Web 服務](../core/publishing-an-orchestration-as-a-web-service.md)   
 [如何使用 BizTalk Web 服務發佈精靈發佈為 Web 服務的協調流程](../core/publish-orchestration-as-web-service--biztalk-web-services-publishing-wizard.md)