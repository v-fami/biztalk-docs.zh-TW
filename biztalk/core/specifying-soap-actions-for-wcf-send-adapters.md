---
title: "指定的 SOAP 動作，wcf 傳送配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send adapters, mapping
- send adapters, WCF services
- mapping, send adapters
- mapping, WCF send adapters
ms.assetid: fa9878eb-65b5-4ccc-b727-ff7e09ba6302
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385e92f7801dc2512fbd038bd0b005d95c503e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="specifying-soap-actions-for-wcf-send-adapters"></a>指定 WCF 傳送配接器的 SOAP 動作
您可以設定**WCF。動作**WCF 傳送配接器傳輸屬性 對話方塊中，或在協調流程中的內容屬性**運算式**圖形。 如果您設定**WCF。動作**協調流程中的內容屬性，您需要讓**動作**WCF 配接器傳輸屬性對話方塊中的靜態傳送埠的空白欄位。 如果也指定動作之靜態傳送埠中， **WCF。動作**將會覆寫您在協調流程中設定的內容屬性。  
  
 此外，有兩種方式來指定這個屬性： 單一動作格式和動作對應格式。 如果您以單一動作格式設定這個屬性 (例如，http://MyService/IMyContract/MyAction1)，外寄訊息之 [WCF 傳送配接器傳輸屬性] 對話方塊中的 SOAP 動作，便會永遠設定為此屬性的指定值。 或者，您可以設定於協調流程的單一動作格式**運算式**圖形。 例如，  
  
```  
OutboundMessage(WCF.Action)="http://MyService/IMyContract/MyAction1";  
```  
  
 如果您以動作對應格式設定這個屬性外, 寄 SOAP 動作由**BTS。作業**內容屬性。 例如，如果這個屬性設定為下列 XML 格式，在 WCF 傳送配接器傳輸屬性對話方塊和**BTS。作業**屬性設定為**Operation_1** WCF 傳送配接器在傳送埠協調流程中，針對外寄 SOAP 動作使用 http://MyService/IMyContract/MyAction1。  
  
```  
BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<Operation Name="Operation_1" Action="http://MyService/IMyContract/MyAction1" />  
<Operation Name="Operation_2" Action="http://MyService/IMyContract/MyAction2" />  
<Operation Name="Operation_3" Action="http://MyService/IMyContract/MyAction3" />  
</BtsActionMapping>  
```  
  
 指定動作對應**WCF。動作**中**運算式**圖形不支援。 您必須在 [WCF 傳輸屬性] 對話方塊中指定動作對應。 WCF 配接器將會使用查詢的 SOAP 動作，然後**BTS。作業**內容屬性，協調流程設定在傳送訊息的連接埠上作業的名稱。  
  
 如果外寄訊息路由傳送以內容為基礎的路由 (CBR) 其中**http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation**未設定屬性，WCF 傳送配接器會將整個動作對應外寄 WCF 訊息的動作字串。 若要解決這個問題，您可以執行下列一種方法：  
  
-   將傳送埠上的動作欄位設定為 http://MyService/IMyContract/MyAction1。  
  
-   設定**BTS。作業**管線中的內容屬性。 例如，設定的值**http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation**為 Operation1。  
  
-   將動作欄位保留空白，並且改用內送訊息中的動作。  
  
 您也可以使用 [BizTalk WCF 服務使用精靈]，來搭配使用 WCF 服務與單一動作或動作對應。 如需詳細資訊，請參閱[如何使用 BizTalk WCF 服務使用精靈來取用 WCF 服務](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設定動態傳送埠使用 WCF 配接器內容屬性](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)