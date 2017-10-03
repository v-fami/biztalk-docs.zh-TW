---
title: "建構 Web 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, about Web messages
- Web messages, message types
- Web services, Web messages
- Web messages, parts
- Web messages
- messages, Web messages
ms.assetid: ca1792be-5fba-4f5d-a88e-b854f6a8ce33
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c344bbb836a6524ec1fd2656a5ba3f8bc8fad7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-web-messages"></a>建構 Web 訊息
您會從 Web 訊息類型建構 Web 訊息。 新增 Web 參考時，BizTalk 會根據所新增 Web 服務的 Web 方法，自動建立 Web 訊息類型。 您會在協調流程中新增 Web 訊息，並將訊息類型設定為其中一個 Web 訊息類型。 您會根據基本 .NET 或結構描述類型，建立個別的訊息部分。 您也可以建構不含任何訊息部分的 Web 訊息。  
  
 **Web 訊息類型**  
  
 Web 訊息類型是在 Reference.odx 中定義，除了無法修改、重新命名或刪除之外，與一般訊息類型完全相同。 若要刪除 Web 訊息類型，必須從 BizTalk 專案中移除 Web 參考。  
  
 BizTalk 專案會針對該新增 Web 服務中的每個 Web 方法，分別建立一個要求和一個回應 Web 訊息類型。 如果 Web 方法是單向作業，BizTalk 將只會建立要求 Web 訊息類型。 要求 Web 訊息類型會針對 Web 方法的各個輸入參數，分別包含一個訊息部分。 回應 Web 訊息類型則包含傳回值的一個訊息部分，並針對 Web 方法的各個輸出參數，分別包含一個訊息部分。  
  
 BizTalk 會根據不同的 Web 方法參數 (輸入或輸出)，從基本 .NET 類型或結構描述類型建立 Web 訊息類型。 如果 Web 方法參數是基本 .NET 類型，訊息部分就會使用基本 .NET 類型。 如果 Web 方法參數是結構描述類型，BizTalk 就會將該結構描述類型加入至 BizTalk 專案來做為 Reference.xsd 中的結構描述。 結構描述是訊息部分的基礎。 您可以在 Web 參考資料夾中找到 Reference.xsd。  
  
 或者，您也可以藉由呼叫 .NET 類別，同時建立基本類型和結構描述 .NET 類型。 如需有關使用.NET 類別建立訊息類型的詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
 **Web 訊息**  
  
 當您使用 (呼叫) Web 服務時，您就會使用 Web 訊息。 在協調流程中加入 Web 訊息與加入一般訊息的方式相同，唯一差異是訊息類型要設定為 BizTalk 在您加入 Web 參考時所建立的其中一種 Web 訊息類型。  
  
 **訊息部分**  
  
 建立 Web 訊息之後，您可以建構個別的訊息部分。 訊息部分使用基本.NET 類型，如果您使用**訊息指派**圖形。 訊息部分使用結構描述型別，如果您使用**轉換**圖形或**訊息指派**圖形。 如需詳細資訊，請參閱[使用者程式碼中的 建構訊息](../core/constructing-messages-in-user-code.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何新增 Web 訊息](../core/how-to-add-web-messages.md)  
  
-   [如何判斷 Web 訊息部分類型](../core/how-to-determine-a-web-message-part-type.md)  
  
-   [如何建構 Web 訊息部分，從基本.NET 類型](../core/how-to-construct-a-web-message-part-from-a-primitive-net-type.md)  
  
-   [如何建構 Web 訊息部分的結構描述型別](../core/how-to-construct-a-web-message-part-from-a-schema-type.md)  
  
-   [如何建構不含訊息部分的 Web 訊息](../core/how-to-construct-a-web-message-with-no-message-parts.md)