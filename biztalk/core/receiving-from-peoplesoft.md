---
title: "接收來自 PeopleSoft |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9acc71ec-05b8-4490-b3ba-0ce7f27a5a6a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca87df1875f648abe2a986fb0d94b16865ee72f
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="receiving-from-peoplesoft"></a>從 PeopleSoft 接收
Microsoft Adapter for PeopleSoft Enterprise 為傳送配接器。 配接器支援請求-回應，以便您可以先傳送查詢，並取得回應。 不過，如果您只想接收來自 PeopleSoft 的資料，則必須採取額外兩個步驟：  
  
1.  使用「設定命名空間」管線元件，建立自訂接收管線。  
  
2.  建立可從 PeopleSoft 存取的接收埠，例如使用 HTTP 配接器的連接埠。 將自訂接收管線與此接收埠搭配使用。  
  
## <a name="set-namespace-pipeline-component"></a>設定命名空間管線元件  
 接收自 PeopleSoft 的訊息不包含命名空間。 「設定命名空間」管線元件可讓您將命名空間新增至內送訊息。  
  
 「設定命名空間」管線元件的預設位置是 C:\Program Files\Microsoft BizTalk Adapters for Enterprise Applications\Pipeline Component。 您需要將 Microsoft.BizTalk.Adapters.Pipeline.SetNSForMsg.dll 元件複製到 BizTalk 所使用的管線元件目錄。 您還需要將此元件新增至 Visual Studio 工具箱，才能在 [管線設計師] 中使用該元件。  
  
 元件的安裝位置的相關資訊，請參閱[部署管線元件](../core/deploying-pipeline-components.md)。  
  
 如需將元件加入至 Visual Studio 工具箱，請參閱[如何使用 [工具箱]](../core/how-to-use-the-toolbox.md)。  
  
## <a name="configure-the-set-namespace-pipeline-component"></a>設定設定命名空間管線元件  
 「設定命名空間」管線元件有兩個屬性可讓您設定：  
  
|使用|動作|  
|--------------|----------------|  
|**預設目標命名空間**|將固定的命名空間放在內送訊息中。|  
|**目標命名空間的 XPath**|根據 XPath 指定的位置，從內送訊息中擷取命名空間。 元件若是找不到有效的命名空間，就會在應用程式事件日誌中記錄警告，並使用預設目標命名空間 (若已指定)。|  
  
 如果您將這兩個屬性保留空白，則元件不會指派命名空間給內送訊息，但是會將警告寫入至應用程式事件日誌。  
  
## <a name="see-also"></a>另請參閱  
 [開發應用程式](../core/developing-applications4.md)