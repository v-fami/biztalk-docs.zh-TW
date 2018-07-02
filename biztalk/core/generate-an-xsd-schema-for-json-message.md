---
title: 產生 JSON 訊息的 XSD 結構描述 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5453b76c-b282-442f-9eb1-6c2628b38ad5
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b95af2f3a44454aa59138cd6f77b7f7195cbb02b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971135"
---
# <a name="generate-an-xsd-schema-for-json-message"></a>產生 JSON 訊息的 XSD 結構描述
> [!NOTE]
>  本教學課程僅適用於 BizTalk Server。  
  
 在此解決方案中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式接收 JSON 訊息。 應用程式可以處理訊息之前，它必須轉換成 XSD 結構描述。 若要這樣做，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]所提供的 JSON 結構描述精靈建立 XSD 結構描述從 JSON 訊息。  
  
1. 在 Visual Studio 中，建立新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。  
  
2. 在 [方案總管] 中，以滑鼠右鍵按一下專案名稱 >**新增** > **新項目** > **JSON 結構描述精靈**。 提供的結構描述的名稱 (`PO.xsd`)，然後按一下**新增**。  
  
3. 在 JSON 結構描述精靈中，在 歡迎使用 頁面上，按一下**下一步**。  
  
4. 在 [JSON 結構描述資訊] 頁面中，會提供傳送至 JSON 採購訂單檔案的位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。 提供根節點名稱，而目標命名空間，然後按**完成**。  
  
    ![產生的 XSD 結構描述 json](../core/media/btsjson-wizard.png "BTSJSON_Wizard")  
  
5. 具有指定名稱的結構描述新增至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]專案。 產生的結構描述檔案 (**PO.xsd**) 也會提供範例。  
  
## <a name="see-also"></a>另請參閱  
 [使用 BizTalk Server 處理 JSON 訊息](../core/processing-json-messages-using-biztalk-server.md)