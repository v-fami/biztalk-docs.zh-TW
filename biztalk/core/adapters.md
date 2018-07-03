---
title: 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- adapters
- send adapters
- adapters, about adapters
- send adapters, about send adapters
- receive adapters, about receive adapters
- adapters, adapter framework
- receive adapters
- adapters, send adapters
ms.assetid: 7803a806-3396-4662-877f-eae11cb5e3e4
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c16fc3dd95145d35bd09aeb049d7d38df979e6a0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022932"
---
# <a name="adapters"></a>配接器
Microsoft BizTalk Server 使用配接器的概念與外部系統、應用程式和實體交換訊息。 *配接器*都是 COM 或。以.NET 為基礎的元件傳送商務端點 （例如檔案系統、 資料庫和自訂商務應用程式） 的訊息，使用各種通訊協定。  
  
 BizTalk Server 使用配接器以傳送和接收作業與外部實體交換訊息。  
  
-   BizTalk Server 使用配接器支援的通訊協定，將資訊傳送至外部實體時，即為發生傳送 (或傳送端) 作業。  
  
-   當配接器收到來自外部實體的資訊，並將它傳送至「BizTalk Server 傳訊引擎」時，即為發生接收 (或接收端) 作業。  
  
## <a name="the-adapter-framework"></a>配接器架構  
 下圖顯示配接器和「配接器架構」如何共同運作，將應用程式連線至 BizTalk Server。  
  
1. 資料是透過接收位置接收，該位置在指定的位址聆聽特定通訊協定的訊息。 接收位置與配接器和接收管線相關聯。 您可以設定配接器和管線元件，對已預先決定通訊協定的訊息執行特定邏輯。  
  
2. 接收位置收到訊息後，便會將訊息傳送至配接器，而建立新的 BizTalk Server 訊息，將資料流附加到訊息 (通常在訊息的內文部分)，新增與接收資料的結束點相關的任何中繼資料，然後將該訊息提交至「傳訊引擎」。  
  
3. 傳訊引擎將訊息傳送到接收管線，讓資料在此轉換成 XML，並在此驗證訊息傳送者、解密訊息及驗證 XML。  
  
4. 「傳訊引擎」將訊息發佈至 MessageBox。 MessageBox 是一個 Microsoft SQL Server 資料表，其中包含要處理的訊息。 協調流程和傳送埠兩者都可以訂閱 MessageBox。  
  
5. 傳訊引擎根據符合訂閱者在篩選條件中設定之規格的訊息內容屬性，將訊息傳送到協調流程或傳送埠訂閱者。  
  
6. 若協調流程為訂閱者，協調流程會處理訊息並使用傳送埠將訊息傳送出去。 當訊息抵達傳送埠或當傳送埠是唯一的訂閱者時，會先透過傳送管線將訊息傳送到傳送配接器，之後才會在網路上傳輸。  
  
   配接器架構  
  
   ![配接器架構](../core/media/ebiz-sdk-adpttoday.gif "ebiz_sdk_adpttoday")  
  
## <a name="receive-adapters"></a>接收配接器  
 接收配接器負責將網路/資料來源資料流附加到訊息內文，以建立新的 BizTalk Server 訊息。 它也會新增與接收資料的結束點有關的任何中繼資料，然後將該訊息提交至傳訊引擎。  
  
 配接器將接收結束點的資料刪除，或是將適當的通知訊息傳送到用戶端，以表示 BizTalk Server 已接受資料。  
  
## <a name="send-adapters"></a>傳送配接器  
 傳送配接器負責使用其特定的傳輸通訊協定，將 BizTalk 訊息傳送到指定的結束點。  
  
 如需有關配接器的詳細資訊，請的結構，配接器，以及撰寫自訂配接器，請參閱[開發自訂配接器](../core/developing-custom-adapters.md)。  
  
## <a name="see-also"></a>另請參閱  
 [成品](../core/artifacts.md)