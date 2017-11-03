---
title: "訊息 訊息指派圖形中的參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, code samples
- code samples, messages
- messages, objects
ms.assetid: 428f7eb8-001e-4147-b1c8-f9bb6f3a80f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b834eefa991b6cad89a04a836f63d1b9af73fc04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-references-in-message-assignment-shape"></a>訊息指派圖形中的訊息參考
當您首次將以 .NET 為基礎的物件指派到訊息或訊息部分時，該訊息便會保留並維護物件的參考。  
  
 為了效率和延展性，協調流程引擎不會執行 「 深層複製 」 物件的： 也就是說，它不會複製物件的整個內容的訊息。  
  
 如果您接著將物件指派到另一個訊息或訊息部分，針對原始物件的任何修改都會造成第二個訊息或訊息部分的修改。 您應該避免這種做法，因為結果會是無法預期的。  
  
 如果需要讓第二個訊息具有物件的不同複本，您就應該將第一個訊息或訊息部分指派給第二個訊息或訊息部分。  
  
 請設想下列範例：  
  
 錯誤方式：  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myObj; // assign the second message (wrong!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 在此情況下，myMsg2.myInt 已經遭到覆寫，而且現在具有 5 的值。  
  
 正確方式：  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myMsg1; // assign the second message (right!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 在此情況下，myMsg2.myInt 依然具有 100 的值，這點與預期相同。  
  
## <a name="see-also"></a>另請參閱  
 [建構訊息](../core/constructing-messages.md)