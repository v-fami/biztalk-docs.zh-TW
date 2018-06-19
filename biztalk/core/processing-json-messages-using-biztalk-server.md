---
title: 處理 JSON 訊息使用 BizTalk Server |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6db1421-9478-477c-8645-09eefba06246
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c2e4adac7c7d1503a49f68208e45e09f86b67ac
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26007151"
---
# <a name="processing-json-messages-using-biztalk-server"></a>使用 BizTalk Server 處理 JSON 訊息
> [!NOTE]
>  本教學課程僅適用於 BizTalk Server。  
  
 本教學課程示範如何使用 JSON 訊息處理[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本教學課程會使用與 BizTalk Server 現在可用的自訂管線元件。 這些管線元件會將 JSON 訊息轉換成 XML (接收到訊息時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程，並將訊息從 XML 轉換為 JSON，時送出訊息。  
  
## <a name="what-does-this-tutorial-do"></a>此教學課程，請執行有哪些功能？  
 為了示範 JSON 處理中，我們建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行下列命令，依指定的順序：  
  
1.  接收 JSON 訂單，並在接收管線中，使用 JSON 解碼器元件來轉換 XML 訊息之 JSON 訊息。  
  
2.  將 XML 訂單轉換成使用對應的 XML 發票。  
  
3.  在傳送管線中，使用 JSON 編碼器來轉換 XML 發票為 JSON 發票及送出。  
  
 ![處理 JSON 訊息在 BizTalk Server](../core/media/btsjson-flow.png "BTSJSON_Flow")  
  
## <a name="how-to-use-this-tutorial"></a>如何使用這個教學課程？  
 本教學課程建立範例 (**BTSJSO**) 可以從下載[MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197)。 您無法使用範例，再進行此教學課程來了解範例的建置方式。 或者，您可以使用本教學課程建立您自己的解決方案從頭。 本教學課程的目標傾向第二種方法，讓您了解這個方案的建置方式。 此外，盡可能，教學課程與範例一致，並使用相同的成品 （例如，結構描述、 轉換） 名稱做為範例中。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [產生 JSON 訊息的 XSD 結構描述](../core/generate-an-xsd-schema-for-json-message.md)  
  
-   [建立自訂管線來處理 JSON 訊息](../core/create-custom-pipelines-to-process-json-messages.md)  
  
-   [建立 BizTalk Server 協調流程](../core/create-a-biztalk-server-orchestration.md)  
  
-   [部署和測試應用程式](../core/deploy-and-test-the-application.md)  
  
## <a name="see-also"></a>請參閱  
 [BizTalk Server 教學課程](../core/biztalk-server-tutorials.md)