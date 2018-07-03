---
title: 處理 JSON 訊息使用 BizTalk Server |Microsoft Docs
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
ms.openlocfilehash: db57847964c7e3da452675945b7d4557ae7cbc85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986343"
---
# <a name="processing-json-messages-using-biztalk-server"></a>使用 BizTalk Server 處理 JSON 訊息
> [!NOTE]
>  本教學課程僅適用於 BizTalk Server。  
  
 本教學課程示範如何處理使用 JSON 訊息[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 本教學課程會使用現在可以搭配 BizTalk Server 使用的自訂管線元件。 這些管線元件會將 JSON 訊息轉換成 XML (接收到訊息時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協調流程，並將訊息從 XML 轉換為 JSON，同時送出訊息。  
  
## <a name="what-does-this-tutorial-do"></a>此教學課程，請執行有哪些功能？  
 為了示範 JSON 處理，我們建立[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會執行下列命令，以指定的順序：  
  
1. 接收 JSON 訂單，並在接收管線中，使用 JSON 解碼器元件來轉換 XML 訊息的 JSON 訊息。  
  
2. XML 訂單轉換為使用對應的 XML 發票。  
  
3. 在傳送管線中，將 XML 轉換的 JSON 編碼器發票到 JSON 使用發票，並傳送出去。  
  
   ![處理 JSON 訊息，BizTalk Server 中的](../core/media/btsjson-flow.png "BTSJSON_Flow")  
  
## <a name="how-to-use-this-tutorial"></a>如何使用本教學課程？  
 本教學課程中建置範例 (**BTSJSO**)，您可以從下載[MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=403197)。 您可以使用範例，並進行此教學課程，以了解如何建置範例。 或者，您可以使用本教學課程來建立您自己的解決方案由下而上。 本教學課程的目標傾向第二種方法，讓您了解如何建置此解決方案。 此外，盡量，本教學課程與範例一致，並使用相同名稱的成品 （例如，結構描述、 轉換） 範例中使用。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [產生 JSON 訊息的 XSD 結構描述](../core/generate-an-xsd-schema-for-json-message.md)  
  
-   [建立自訂管線來處理 JSON 訊息](../core/create-custom-pipelines-to-process-json-messages.md)  
  
-   [建立 BizTalk Server 協調流程](../core/create-a-biztalk-server-orchestration.md)  
  
-   [部署和測試應用程式](../core/deploy-and-test-the-application.md)  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 教學課程](../core/biztalk-server-tutorials.md)