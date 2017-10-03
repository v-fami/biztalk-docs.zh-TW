---
title: "EDI 訊息驗證 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71f34561-d280-48bb-b1dd-ce37b87c5023
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21439969bc8e23b5b9901077c14a98128aa64c2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="edi-message-validation"></a>EDI 訊息驗證
EDI 資料是以分隔檔案形式 (不含自我描述標記) 傳輸，因此，編碼規則會強制套用限制格式設定規則，確保目的地應用程式可以成功地剖析和使用該資訊進行下游處理。  
  
 在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI 的 EDI 接收管線和 EDI 傳送管線，會與 AS2 一起執行一連串的驗證。 有些驗證一定會執行，有些驗證則要在協議屬性或是結構描述中有啟用時才會執行。 如需有關驗證的設定方式的詳細資訊，請參閱[如何驗證 EDI 交換設定](../core/how-validation-of-an-edi-interchange-is-configured.md)。  
  
 EDI 交換的驗證作業包括了幾種不同的驗證方式，如下列主題所述。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [EDI 交換的驗證設定的方式](../core/how-validation-of-an-edi-interchange-is-configured.md)  
  
-   [EDI 結構驗證](../core/edi-structural-validation.md)  
  
-   [協議屬性驗證](../core/agreement-properties-validation.md)  
  
-   [EDI 類型 （資料元素） 驗證](../core/edi-type-data-element-validation.md)  
  
-   [擴充 (BTS-XSD) 驗證](../core/extended-bts-xsd-validation.md)  
  
-   [結構描述驗證](../core/schema-validation2.md)  
  
-   [交叉驗證欄位區段](../core/cross-field-segment-validation.md)