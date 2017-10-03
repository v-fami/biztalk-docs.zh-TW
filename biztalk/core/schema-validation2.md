---
title: "結構描述 Validation2 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2f9d1576-10df-4c5a-9ae0-618f0dd54b4e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 317fa8e0e5e557993922bba383ebf5eca460fa69
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="schema-validation"></a>結構描述驗證
EDI 接收管線和 EDI 傳送管線會使用下列結構描述驗證訊息：  
  
-   **信封驗證**： 服務結構描述中`Microsoft.BizTalk.Edi.BaseArtifacts.dll`中[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]  
  
-   **交易集驗證**： 結構描述中的訊息結構描述儲存在[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI  
  
-   **通知訊息驗證**: CONTRL、 997 和 TA1 結構描述中的`Microsoft.BizTalk.Edi.BaseArtifacts.dll`。  
  
 中的結構描述`Microsoft.BizTalk.Edi.BaseArtifacts.dll`安裝程式會自動部署。 這些結構描述中所列**結構描述**節點**BizTalk EDI 應用程式**中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。  
  
 若要使用的訊息結構描述，您必須安裝它們在您的伺服器的硬碟機上執行中的 MicrosoftEdiXSDTemplates.exe 自動解壓縮檔案[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI 資料夾，然後將其部署專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
 **結構描述判斷**  
  
 當 EDI 接收管線處理接收訊息時，它會判斷要用於透過協議尋查和結構描述探索程序處理訊息的結構描述的命名空間。 如需詳細資訊，請參閱[協議解析、 結構描述探索和授權接收 EDI 訊息](../core/agreement-resolution-schema-discovery-and-authorization-for-received-edi.md)。  
  
 當 EDI 傳送管線建立要傳送的訊息時，它會使用協議屬性填入信封，，並接著執行結構描述驗證資訊的交易集內。 之後載入結構描述，傳送管線會驗證協議屬性 （或後援協議，如果已指定沒有協議） 結構描述。 如果結構描述通過驗證，則管線會對照結構描述驗證交易集。  
  
## <a name="see-also"></a>另請參閱  
 [EDI 訊息驗證](../core/edi-message-validation.md)