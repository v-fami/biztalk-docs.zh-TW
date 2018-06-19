---
title: 如何使用運算式來建立物件和呼叫物件方法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, parameters
- Expression shape [Orchestration Designer], calling objects
- Expression shape [Orchestration Designer], parameters
- Expression shape [Orchestration Designer], passing messages
- orchestrations, methods
- Expression shape [Orchestration Designer], calling methods
- orchestrations, objects
- Expression shape [Orchestration Designer], warning
- Use Default Constructor property
- .NET member invocation
ms.assetid: b6af67eb-8ba5-4c95-9b63-26ebb6617af0
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b56cfa46098569863106485fef204f72b23a4ef5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256606"
---
# <a name="how-to-use-expressions-to-create-objects-and-call-object-methods"></a>如何使用運算式建立物件和呼叫物件方法
您可能需要使用運算式來建立物件或呼叫方法。  
  
## <a name="creating-objects"></a>建立物件  
 若要建立具有這個類別是.NET 類別類型的變數，您可以建構中的物件**運算式**圖形。 您的 .NET 類別變數屬性會包含一個建構函式。 使用預設的建構函式時，只要和宣告其他變數 (像是類型 bool 或 int 中的其中一項) 一樣直接宣告變數即可。  
  
 如果您使用會採用參數的建構函式，您必須使用關鍵字**新**，後面接著 object 類別以及括號括住的任何參數：  
  
```  
new MyClass(myParam1, myParam2)  
```  
  
> [!CAUTION]
>  **使用預設建構函式**執行動作，事實上，某些物件具有建構函式，可能不會顯示屬性。 在此情況下，會自動使用預設建構函式，而且若您嘗試使用不同的建構函式，就會發生錯誤。  
  
## <a name="invoking-methods"></a>呼叫方法  
 若要呼叫 .NET 類別物件上的方法，請在物件參考上附加一個句號和方法名稱，後面跟著以括號括住的任何參數：  
  
```  
MyObject.MyMethod (param1)  
```  
  
## <a name="passing-and-using-messages-as-parameters"></a>以參數傳送和使用訊息  
 若要以參數將訊息傳送給 .NET 類別上的方法呼叫，請先在定義該類別的專案上新增 Microsoft.XLANGs.BaseTypes.dll 的參考，然後在方法簽章中使用類型 XLANGMessage。  
  
 使用類型 XLANGPart 參考多部分訊息類型，可讓您存取訊息的各個部分：  
  
```  
MyMethod(XLANGMessage myMsg)  
{  
XLANGPart myPart = myMsg["Part1"];  
XmlDocument xmlDoc = (XmlDocument) myPart.RetrieveAs(typeof(XmlDocument));  
}  
```  
  
 在呼叫本身中，您只需向對其他參數一樣提供訊息的名稱即可：  
  
```  
MyObject.MyMethod(myMessage)  
```  
  
 您也可以類型 XLANGPart 來傳送訊息部分。  
  
## <a name="net-member-invocation"></a>.NET 成員呼叫  
 您可以存取公用成員，除非在直接存取訊息部分的成員。 若要直接存取訊息部分的成員，就必須將它升級為辨別欄位。  
  
## <a name="comcom-component-invocation"></a>COM/COM+ 元件叫用  
 XLANGs 會產生 C# 程式碼。 所有使用者宣告的 XLANGs 變數都會以 C# 變數的形式產生。 除了在不可部分完成的交易中以外，並沒有任何特殊的行為。 當服務元件 (也就是實作的類別執行個體**System.EnterpriseServices.ServicedComponent**)，然後只宣告中不可部分完成的範圍，則不會 XLANGs 產生及使用真正的 DTC COM + 交易。  
  
 如果變數在不可部分完成的範圍內當做左值 (L-value，也就是寫入的值) 來參考，但是宣告於外部範圍時，會複製該變數來支援復原。 不過，物件 (例如**XmlDocument**) 可以修改.NET 函式呼叫中參數，當做傳遞時的內部，因此，xlangs 將寫入物件，它將不會正確復原。 此情況的解決方法是將這類物件傳遞為 ref 參數。  
  
 這裡的底線為元件的行為應該與在其他 C# 程式中一樣。  
  
## <a name="see-also"></a>另請參閱  
 [關於 BizTalk 訊息內容屬性](../core/about-biztalk-message-context-properties.md)